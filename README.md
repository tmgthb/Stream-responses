# Stream OPENAI API responses for ChatGPT API & InstructGPT models
The code is to demonstrate usage of streaming with ChatGPT API model and I wrote comparable code using the current InstructGPT model. 

## Pre-requisites:
The approach uses only openai and time libraries and re-prints the streams using print(end='', flush=True):
![image](https://user-images.githubusercontent.com/46755670/224536896-19780308-1893-447e-a58b-8970a659eb5c.png)

Disclaimer: The downside of streaming in production usage is the control of appropiate usage policy: https://beta.openai.com/docs/usage-guidelines, which should be reviewed in advance for each application, so I suggest to take a look this policy prior deciding to use streaming. 

## How to stream ChatGPT API model (gpt-3.5-turbo) responses? 
Run the file streams.ipnyb second part. Add user input and you should see similar to below:
![image](https://user-images.githubusercontent.com/46755670/224536853-929d4f4b-1cca-4d40-95ab-1d9d58e700a2.png)

There is no need to print the final empty string through the print().


## How to stream InstructGPT API model (text-davinci-003) responses? 
Run the file streams.pnyb final part. Add user input and you should see similar to below:
![image](https://user-images.githubusercontent.com/46755670/224536590-bbe76d52-4356-4b0c-a0c0-e3aefbeb178b.png)

## Suggestions and improvements
Feel free to fork and further improve the code as per the license. For example you can further improve the ChatML to ensure the flow follows desired "system" rules. I left these empty now to make this basic script very generic. See as well [my article](https://tmmtt.medium.com/how-to-stream-chatgpt-api-responses-b783f1e5f13d) in Medium.
