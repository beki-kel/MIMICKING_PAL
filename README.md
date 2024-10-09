## MIMICKING PAL With Prompt Engineering 

## INTRODUCTION 
PAL is a novel method that uses an LLM to read natural language problems and generate programs as reasoning steps, but offload the solution step to a Python interpreter. 
This notebook tries to show how PAL operates by using the example of currency exchange prompts. It uses the Exchange Rate API to get real-time exchange rates and Google Gemini to provide prompt engineering. 
It calculates currency conversion rates for different currencies and provides a structured environment for prompt engineering tasks.

## Features
- Tried to mimic PAL by creating a response-like program (python)
- I ensure that variable names in the prompt meaningfully reflect their roles. This keeps the generated code linked to the entities in the question.
- Integrate **Google Gemini** for prompt engineering ( few-shot learning ) and **EXCHANGE RATE API** for real-time rate.

## Requirements

- Python 3.8 or higher
- An API key for Exchange Rate API
- An API key for Google Gemini

## Usage

1. Clone the repository:
   ```bash
   git clone https://github.com/beki-kel/MIMICKING_PAL
   ```
2. open the notebook in GOOGLE COLAB


For a better experience use [The Google COLAB LINK](https://colab.research.google.com/drive/17InluIOGKWAitWlLRA-nJwXhlc_epSkh?usp=sharing)

## Explanation of each sections

  #### IMPORTING AND INSTALLING ESSENTIAL PACKAGES:
  - this sectio is to  install and import packages

  #### INTIALIZING API KEYS
  - To make this step work add your api key to the secrets tab in colab like the following par
      ``` bash
        EXCHANGE_RATE_API_KEY = YOUR_API_KEY
        GEMINI_API_KEY = YOUR_API_KEY
      ```
  - In this step the llm params are set after expermenting using suggestion from the documentation

  #### FEW SHOT LEARNING: PROVIDNG THE PROMPTS
   -  This setcion provide prompt generated with the few shot learning architecture.
   -  There are 3 different prompts each are questions answer pairs
   -  The Answers are python codes to solve each problems
   -  The **QUESTIONS** ARE
         ``` bash
            "I have 20 USD and 500 EUR. I am planning to move to Ethiopia. How much will the money I have be worth in Ethiopia?"
            "I have 50 USD, 300 EUR, and 100 GBP. I am planning to move to Japan. How much will this money be worth there, considering the current exchange rates?"
            "I have 1000 in Australia’s currency, 400 in Canada’s currency, and 1500 in Japan’s. After moving to Ethiopia, I want to know the total worth of my money in ETB, considering the current exchange rates?"
            "I have savings in Switzerland, India, and South Africa. I plan to relocate to Ethiopia soon and would like to know how much my savings would be worth there. I have 500 in Switzerland, 70,000 in India, and 2,500 in South Africa. Could you calculate the total value of my savings in Ethiopian Birr, given the current exchange rates?" 
        ```
  #### LLM RESPONSE FOR THE PROMPT
   - This will generate reponse from the llm for the last question which is not mapped with an answer.
   - finally clean the string and use the ``` EXEXC()``` python function to run the response

