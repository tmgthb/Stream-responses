# Stream GPT-4, ChatGPT and GPT-3.5 responses (OPENAI API)
The code is to demonstrate usage of streaming with GPT-4 API, ChatGPT API and InstructGPT (GPT-3.5.) models.

## Pre-requisites:
The approach uses only openai and time libraries and re-prints the streams using print(end='', flush=True):

```
!pip install --upgrade openai
import openai
import time
openai.api_key = user_secrets.get_secret("OPENAI_API_KEY")
startime = time.time()
```
Disclaimer: The downside of streaming in production usage is the control of appropiate usage policy: https://beta.openai.com/docs/usage-guidelines, which should be reviewed in advance for each application, so I suggest to take a look this policy prior deciding to use streaming. 

## How to stream GPT-4 API model (gpt-4 or gpt-4-32k & gpt-4-32k-0314) responses? 

Run the file streams.ipnyb first part. 

```
### STREAM GPT-4 API RESPONSES
delay_time = 0.01 #  faster
max_response_length = 8000
answer = ''
# ASK QUESTION
prompt = input("Ask a question: ")
start_time = time.time()

response = openai.ChatCompletion.create(
    # GPT-4 API REQQUEST
    model='gpt-4',
    messages=[
        {'role': 'user', 'content': f'{prompt}'}
    ],
    max_tokens=max_response_length,
    temperature=0,
    stream=True,  # this time, we set stream=True
)

for event in response: 
    # STREAM THE ANSWER
    print(answer, end='', flush=True) # Print the response    
    # RETRIEVE THE TEXT FROM THE RESPONSE
    event_time = time.time() - start_time  # CALCULATE TIME DELAY BY THE EVENT
    event_text = event['choices'][0]['delta'] # EVENT DELTA RESPONSE
    answer = event_text.get('content', '') # RETRIEVE CONTENT
    time.sleep(delay_time)
```



After inserting the user input and pressing enter, you should see the output printed:

![image](https://user-images.githubusercontent.com/46755670/225767202-41026ba9-bbf0-4941-ba5b-64d60de539dc.png)


## How to stream ChatGPT API model (gpt-3.5-turbo) responses? 
Run the file streams.ipnyb second part. Add user input and you should see similar to below:
```
### STREAM CHATGPT API RESPONSES
delay_time = 0.01 #  faster
max_response_length = 200
answer = ''
# ASK QUESTION
prompt = input("Ask a question: ")
start_time = time.time()

response = openai.ChatCompletion.create(
    # CHATPG GPT API REQQUEST
    model='gpt-3.5-turbo',
    messages=[
        {'role': 'user', 'content': f'{prompt}'}
    ],
    max_tokens=max_response_length,
    temperature=0,
    stream=True,  # this time, we set stream=True
)

for event in response: 
    # STREAM THE ANSWER
    print(answer, end='', flush=True) # Print the response    
    # RETRIEVE THE TEXT FROM THE RESPONSE
    event_time = time.time() - start_time  # CALCULATE TIME DELAY BY THE EVENT
    event_text = event['choices'][0]['delta'] # EVENT DELTA RESPONSE
    answer = event_text.get('content', '') # RETRIEVE CONTENT
    time.sleep(delay_time)
```

![image](https://user-images.githubusercontent.com/46755670/225769321-0a361329-3a2e-469a-b6b8-057d121c3179.png)


## How to stream InstructGPT API model (text-davinci-003) responses? 
Run the file streams.pnyb third part. Add user input and you should see similar to below:


```
collected_events = []
completion_text = []
speed = 0.05 #smaller is faster
max_response_length = 200
start_time = time.time()
prompt = input("Ask a question: ")
# Generate Answer
response = openai.Completion.create(
    model='text-davinci-003',
    prompt=prompt,
    max_tokens=max_response_length,
    temperature=0,
    stream=True,  # this time, we set stream=True
)

# Stream Answer
for event in response:
    event_time = time.time() - start_time  # calculate the time delay of the event
    collected_events.append(event)  # save the event response
    event_text = event['choices'][0]['text']  # extract the text
    completion_text += event_text  # append the text
    time.sleep(speed)
    print(f"{event_text}", end="", flush=True)
```


![image](https://user-images.githubusercontent.com/46755670/224536590-bbe76d52-4356-4b0c-a0c0-e3aefbeb178b.png)


## How to create Streamlit app with OpenAI API?
I add a working "app_streamlit.py"-file, which you can fork to your repository with the "requirements.txt" and deploy it in Streamlit. In the advanced settings, add the OPENAI_API_KEY-variable using format: OPENAI_API_KEY = "INSERT HERE YOUR KEY"
![image](https://user-images.githubusercontent.com/46755670/230953129-51775d7d-9585-4e1a-bdcb-9a32a23421c4.png)



## Suggestions and improvements
Feel free to fork and further improve the code as per the license. For example you can further improve the ChatML to ensure the flow follows desired "system" rules. I left these empty now to make this basic script very generic. I recommend to check my articles specific to ChatGPT API about [streaming responses](https://tmmtt.medium.com/how-to-stream-chatgpt-api-responses-b783f1e5f13d) in Medium related to Streaming, [ChatML: guiding prompts with system, assistant and user roles](https://tmmtt.medium.com/chat-markup-language-chatml-35767c2c69a1) and [ChatGPT API introduction tutorial](https://tmmtt.medium.com/chatgpt-api-tutorial-3da433eb041e). 
