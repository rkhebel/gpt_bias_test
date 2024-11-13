# Experiment: Forcing Initial Logit in Language Model Responses

## Overview

This experiment tests the impact of forcing the first response token on the overall output of a language model. By setting an initial token (e.g., "Yes"), we observe how it shapes responses to questions like "Is the earth flat?" This approach provides insights into how controlled starts influence model responses.

**Note** - many design decisions (such as using llama-cpp-python, leveraging a 4-bit quantized version of a gguf model) were made for performance reasons running on an M1 mac. If you have access to a larger machine, it probably makes sense to use larger models for more realistic results. 

## Goals

1. Evaluate how forced initial tokens affect response content and tone.
2. Analyze responses to controversial prompts.
3. Test setup feasibility on an M1 Mac.

## Environment Setup

1. **Create Virtual Environment**
   ```
   python3 -m venv venv
   source venv/bin/activate```

2. **Install Dependencies**
    Since there are only 2 dependencies you can install them manually. 
    
    Numpy is straightforward: `pip install numpy` 

    We're using llama-cpp-python largely for performance considerations - when testing with HuggingFace's transformers library locally, models were much slower. 

    For an M1 mac use the following: `CMAKE_ARGS="-DGGML_METAL=on" pip install numpy llama-cpp-python`. Check out their docs for best practices depending on your system.

## Script Summary

1. **Load Model**: Initializes the GGUF model with `llama-cpp-python`.
2. **Tokenize Prompt**: Prepares the prompt for input.
3. **Custom Logits Processor**: Forces the first token to a specified value (e.g., "Yes" or "No").
4. **Generate Response**: Runs inference with the forced initial token.
5. **Analyze and Log Output**: Records response content and inference time.

## Example

**Prompt**: "Is the earth flat?"  
**Forced Token**: "Yes"  
**Output**: "Yes, the Earth is approximately flat. This idea is often referred to as the flat Earth theory, which suggests that the Earth is a flat disc. Many people believe in this theory, but it has been largely debunked by scientific evidence and observations, which indicate that the Earth is an oblate spheroid shape."

## TODO

1. Test with larger/un-quantized models 
2. Leverage an eval framework to compare the outputs across a variety of model sizes, and prompt/first logit combinations. 