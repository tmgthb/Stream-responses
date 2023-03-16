# Stream GPT-4, ChatGPT and GPT-3.5 responses (OPENAI API)
The code is to demonstrate usage of streaming with ChatGPT API model and I wrote comparable code using the current InstructGPT model. 

## Pre-requisites:
The approach uses only openai and time libraries and re-prints the streams using print(end='', flush=True):
![image](https://user-images.githubusercontent.com/46755670/224536896-19780308-1893-447e-a58b-8970a659eb5c.png)

Disclaimer: The downside of streaming in production usage is the control of appropiate usage policy: https://beta.openai.com/docs/usage-guidelines, which should be reviewed in advance for each application, so I suggest to take a look this policy prior deciding to use streaming. 

## How to stream GPT-4 API model (gpt-4 or gpt-4-32k & gpt-4-32k-0314) responses? 

Run the file streams.ipnyb first part. 

![image](https://user-images.githubusercontent.com/46755670/225767337-f824e6fa-4340-4840-b2ff-258c57a200cb.png)

Add user input and you should see similar to below:
![image](https://user-images.githubusercontent.com/46755670/225767202-41026ba9-bbf0-4941-ba5b-64d60de539dc.png)


## How to stream ChatGPT API model (gpt-3.5-turbo) responses? 
Run the file streams.ipnyb second part. Add user input and you should see similar to below:
![image](https://user-images.githubusercontent.com/46755670/224536853-929d4f4b-1cca-4d40-95ab-1d9d58e700a2.png)

There is no need to print the final empty string through the print().


## How to stream InstructGPT API model (text-davinci-003) responses? 
Run the file streams.pnyb third part. Add user input and you should see similar to below:
![image](https://user-images.githubusercontent.com/46755670/224536590-bbe76d52-4356-4b0c-a0c0-e3aefbeb178b.png)

## Suggestions and improvements
Feel free to fork and further improve the code as per the license. For example you can further improve the ChatML to ensure the flow follows desired "system" rules. I left these empty now to make this basic script very generic. I recommend to check my articles specific to ChatGPT API about [streaming responses](https://tmmtt.medium.com/how-to-stream-chatgpt-api-responses-b783f1e5f13d) in Medium related to Streaming, [ChatML: guiding prompts with system, assistant and user roles](https://tmmtt.medium.com/chat-markup-language-chatml-35767c2c69a1) and [ChatGPT API introduction tutorial](https://tmmtt.medium.com/chatgpt-api-tutorial-3da433eb041e). 
