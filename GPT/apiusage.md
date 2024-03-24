
python 3 才可以用

我的第一个代码版本
```
import openai
openai.api_key = ""// your api key



response = openai.ChatCompletion.create(
    model="gpt-3.5-turbo", 
    messages=[
        {"role": "system", "content": "You are a helpful assistant."},
        {"role": "user", "content": "Please say hello"}
    ]
)

# Extract and print the assistant's response
print(response.choices[0].message['content'])
```


role 只能是以下其中一个

['system', 'assistant', 'user', 'function']




遇到了ssl问题

https://github.com/urllib3/urllib3/issues/3020
