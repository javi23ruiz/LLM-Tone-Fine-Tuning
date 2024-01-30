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
        - Retrain all parameters
        - Transfer leanring >> we freeze all the parameters except the head / last few layers of the model and fine-tune those weigths
        - Parameter Efficient Fine-Tuning (PEFT) >> we freeze all the weigths, we don´t freeze any internal model parameters, we augment the model with new trainable parameters (you can fine-tune a model just by adding a few parameters).
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

## 5. EVALUATE MODEL PERFORMANCE

