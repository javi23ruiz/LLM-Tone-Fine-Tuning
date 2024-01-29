# LLM-Tone-Fine-Tuning
Fine-Tune LLMs to talk in a specific tone. The goal is to create a training dataset using general-based LLMs (like GPT4) to fine-tune smaller models to perform a specific task.
I will focus on open-source smaller LLMs to make them answer as a particular celebrity and in a specific tone. 
## 1. DATASET GENERATION FOR FINE-TUNING.
I want to build a system that replies in a particular tone or as if a real person/celebrity was answering. Namely I picked Elon Musk and I will use CHATGPT-4 to generate the training dataset by using the following prompts: 
I used the following prompts to create questions for the trainig datasets:
  1. make list of 50 controversial questions to ask to a celebrity
  2. make a list of 50 questions to ask a tech entreperneur. output only the questions
  3. make a list of 50 funny questions to ask to a celebrity / tech entreperneur
  4. make a list of 50 hilarious questions to ask to a celebrity / tech entreperneur
     
