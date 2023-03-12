# Stream OPENAI API responses for ChatGPT API & InstructGPT models
The code is to demonstrate usage of streaming with ChatGPT API model and I wrote comparable code using the current InstructGPT model.

## Pre-requisites:
The approach uses only openai and time libraries and re-prints the streams using print(end='', flush=True):
![image](https://user-images.githubusercontent.com/46755670/224536896-19780308-1893-447e-a58b-8970a659eb5c.png)


## How to stream ChatGPT API model (gpt-3.5-turbo) responses? 
Run the file streams.ipnyb second part. Add user input and you should see similar to below:
![image](https://user-images.githubusercontent.com/46755670/224536853-929d4f4b-1cca-4d40-95ab-1d9d58e700a2.png)



## How to stream InstructGPT API model (text-davinci-003) responses? 
Run the file streams.pnyb final part. Add user input and you should see similar to below:
![image](https://user-images.githubusercontent.com/46755670/224536590-bbe76d52-4356-4b0c-a0c0-e3aefbeb178b.png)


