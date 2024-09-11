# finetuning-LLMs
An indepth understanding of supervised finetuning the large language models.

This notebook consists of an end to end execution of fine tuning an existing LLM models 
with the existing or custom datasets.
*this excercise can be executed at Google Colab with T4 setting*

Here we will first learn 
  ## - Supervised fine tuning an LLM model (SFT)
  ## - Further improve the model's output to align better with human preferences using technique called as "Direct Preference optimization (DPO)"
  ## - Generate responses with the finetuned model


### General steps to follow.
  - Import Libraries
  - Dataset Preparation
       - choose the dataset which will be used to fine tune the models. it should be noted that the effective results would be achieved when the nature of selected data align with the model in consideration.
       - prepara the dataset as per the requirement.
  - set the configurations needed for
       - SFT tuning i.e. the configurations required for the Class used to do SFT(supervised fine tuning)
       - LORA configurations: parameters required when we want to use PEFT techniques to fine tune models
       - training parameters: parameters required for model training
  - load model and tokenizer
  - start the model training
  - if you have used PEFT to train model, do merge trained model with the initial model objects and unload not required auxillary parts.
       - During training with PEFT methods like LoRA, only a subset of the model's parameters (e.g., low-rank matrices in LoRA) is updated, while the original model's parameters remain mostly unchanged. The 
         merge_and_unload() method merges these fine-tuned parameters back into the main model. This means that the original model weights are updated to reflect the changes learned during the PEFT process.
       - Once the fine-tuned parameters are merged into the main model, the additional PEFT-specific components (like the low-rank matrices in LoRA) are no longer needed. The unload() part of the method frees up 
         memory by removing these auxiliary components, reducing the overall footprint of the model.
  - save model checkpoint and tokenizer
  - Inference
       - Format the text and pass it in to generate response.
  
