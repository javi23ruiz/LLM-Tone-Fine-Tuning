# LLM-Tone-Fine-Tuning
Fine-Tune LLMs to talk in a specific tone. The goal is to create a training dataset using general-based LLMs (like GPT4) to fine-tune smaller models to perform a specific task.
I will focus on open-source smaller LLMs to make them answer as a particular celebrity and in a specific tone. We don´t need to rely on a general-base LLM to perform a specific task. A smaller fine-tuned model can outperform a larger general based model (InstructGPT - 1.3B parameters vs GPT3 - 175B parameters).

Ways to fine-tune models
- Self-supervised
- Supervised Fine Tuning: we have a dataset with inputs and outputs >> question-asnwer pairs
- Reinforcement learning

STEPS TO FINE-TUNING A MODEL
1. Choose fine-tuning task
    - TASK >> text generation
2. Prepare training dataset
3. Choose a base model
4. Fine-tune model via supervised learning
    - Options we have when it comes to update the model parameters:
        - Retrain all parameters >> updates all the model weigths (7B model has 7B weigths..) Parameters get updated repeadtedly (go through your data via multiple epochs)
        - Transfer leanring >> we freeze all the parameters except the head / last few layers of the model and fine-tune those weigths
        - Parameter Efficient Fine-Tuning (PEFT) >> we freeze all the weigths, we don´t freeze any internal model parameters, we augment the model with new trainable parameters (you can fine-tune a model just by adding a few parameters). PEFT enables efficient adaptation of pre-trained language models to several downstreams applications without fine-tuning the model's parameters. PEFT methods only fine-tune a samll number of extra model parameters, thereby decreasing the computational and storage cost. 
            - Low-Rank Adaptation > fine-tunes the model by adding new trainable parameters. 
5. Evaluate model performance
    
        
            
## 1. CHOOSE FINE-TUNING TASK
TASK >> text generation

## 2. DATASET GENERATION FOR FINE-TUNING.
I want to build a system that replies in a particular tone or as if a real person/celebrity was answering. Namely I picked Elon Musk and I will use CHATGPT-4 to generate the training dataset by using the following prompts: 
I used the following prompts to create questions for the trainig datasets:
  1. make list of 50 controversial questions to ask to a celebrity
  2. make a list of 50 questions to ask a tech entreperneur. output only the questions
  3. make a list of 50 funny questions to ask to a celebrity / tech entreperneur
  4. make a list of 50 hilarious questions to ask to a celebrity / tech entreperneur
     
## 3. PREPARE DATASET

## 4. FINE-TUNE MODEL VIA SUPERVISED LEARNING

- LoRA (Low Rank Adaptation) >> it freezes all the weigths of the pre-trained llm matrix and fine-tunes two smaller matrices (adpaters). LoRa represents the weigths updates with two smaller matrices through low-rank decomposition. These new matrices are used to adapt to the new data while keeping the number of update params low. These weight changes in trhe new matrices are tracked in **two separte smaller matrcies (low rank matrcies)** that get multiplied together to form a matrix of the same size as the models´s weigth matrix The fine-tuned adapter is loaded to the pretrained model and used for inference, both the original and adapter weigths are combined.
    - As with other methods supported by PEFT, to fine-tune a model using LoRA, you need to:
        1. Instantiate a base model.
        2. Create a configuration (LoraConfig) where you define LoRA-specific parameters.
              - Rank >> as rank increase you train more parameters. Increases the precision. Higher rank is for very complex tasks, with llms that have been trained on a huge amount of data, the model could do the specific task by prompt engineering.
              - From the paper: training all layers of the network is necessary to match performance of full-parameter fine-tuning
              - From LoRA paper >> rank may not matter from 8 to 256.
              - Alpha >> determines a scaling factor before the new weigths get added to the original weights. Scale multiplier = alpha / rank. Microsoft LoRA sets 2XRank. QLoRA is 1 / 4.
              - Dropout to avoid overfitting >> randonmly leaves out some weigths unchanged. 
        4. Wrap the base model with get_peft_model() to get a trainable PeftModel.
        5. Train the PeftModel as you normally would train the base model.
- QLoRA >> more effecient that LoRA where the pretrained model is loaded to GPU as quantized 4-bit weigths (compared to 8 bits weigths of LoRA)
## 5. EVALUATE MODEL PERFORMANCE



####  REFERENCES
https://www.databricks.com/blog/efficient-fine-tuning-lora-guide-llms
https://huggingface.co/docs/peft/main/en/conceptual_guides/lora
https://www.entrypointai.com/blog/lora-fine-tuning/
