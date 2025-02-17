# Week 7: Part 1 - LLM

---------------
#### :dizzy: **Lab Date :** Feb 24, 26
#### :alarm_clock: **Due Date :** 2:00 pm March 3   
#### :pencil: Every group member must be present for every check point.
-------------------

## Task List
> [!CAUTION]
> Pi's Fan will run in full speed. Ensure no objects nearby the fan.

------------------
## 1. Local deploy LLM using ```Ollama```


LLMs consume a lot of memory—we need to remove restrictions in the Pi config file.
<br>In the Terminal, do such:

```shell
sudo su
echo "*               soft   memlock        unlimited" >> /etc/security/limits.conf
echo "*               hard   memlock        unlimited" >> /etc/security/limits.conf
reboot
```
- [ ] **Switch to ```eduroam```  WiFi for LLM model downloading**

I did test last week. Somehow ```iot_lab``` WiFi is slow  specifically for Ollama download. 
<br>You need to switch to ```edueoam``` WiFi to get faster download.

<br>Visit https://cat.eduroam.org/ . Click Download. You need to select "Syracuse University" as the organization.

Then run the downloaded ```eduroam-linux_--Syracuse_University-Eduroam_at_S_U.py``` file. 
<br>It will pop out a window. Enter your syr email and password.


- [ ] **Install ```Ollama```**

Go to the Github page of ```Ollama```:
<br>https://github.com/ollama/ollama  Read thru the webpage.
<br>You should see the intallation is a single line of command.

```shell
curl -fsSL https://ollama.com/install.sh | sh
```

- [ ] **Download models**

On the Github page, you can see a list of models.
<br>For example, if you do Terminal line  ```ollama run llama3.2``` 
<br>It will automatically start downloading and then run the model.
<br>The model will be defaultly downloaded to your ```/usr/share/ollama/.ollama``` folder (you may need to show hidden files.)

Download 2~3 models for later testing. The size should be smaller than 5 GB, such as Llama 3.2 (2.0GB), Gemma 2 (1.6GB).

In command line, use this to check all models downloaded in your local Pi:

```shell
ollama list
```
> [!Note]
> Once finish downloads, switch back to ```iot_lab``` WiFi

## 2. Compare performance in Command Line

- [ ] **Know ```Ollama``` command line**

Type such to check some useful commands:

```shell
cao@raspberrypiCao:~ $ ollama -h
```

```shell
cao@raspberrypiCao:~ $ ollama run --help
```
Check the output of 2nd shell, it provides a ```--verbose``` tool to check token/s.
<br>Two important metrics you need to check are eval count and eval rate. 
<br>For such example, 54 token(s) and 4.52 tokens/s.

```shell
cao@raspberrypiCao:~ $ ollama run llama3.2 --verbose
>>> Help me make an excuse for not attending a lab. Less than 50 words.
Here's a possible excuse:

"Unfortunately, I won't be able to attend the lab today due to unexpected 
issues with my equipment at home, which is being sent out for repair. I'll 
make sure to catch up on any missed work as soon as possible."

total duration:       15.860609422s
load duration:        43.120325ms
prompt eval count:    515 token(s)
prompt eval duration: 3.127s
prompt eval rate:     164.69 tokens/s
eval count:           54 token(s)
eval duration:        11.935s
eval rate:            4.52 tokens/s
```

- [ ] **Test LLM's knowledge in different fields**

Use ```Ollama``` command line to chat with different LLMs that you downloads.

Ask questions in different fields, such as:
* Common knowledge: Is Syracuse closer to Chicago or Boston? / Is Chicken Parm an Italian food?
* Sports: Who scores in 2010 World Cup Final? / Who is the FMVP of 2011 NBA final?
* Engineering math: How to multiply matrix [2, 3; 9, 1]*[-3; 5]? / What is the inverse Laplace of 2/(s+4)?
* Coding: How to use command line to check disk storage in Linux? / Write a Servo control code in Arduino?

You can try to test knowledge in many other fields. For every answer, your group give a rating to it (such as 1-10)

Test at least 5-10 questions in each field. 
<br>Form your averaged eval rate (Tokens/s) and answer ratings in a table form. 
<br>For example:

|  Tokens/s  | LLM 1 | LLM 2 | LLM 3|
| -------- | ------- |------- |------- |
| Field 1 |     |  |  |
| Field 2 |    |  |  |
| Field 3    |     |  |  |

|  Answer rating  | LLM 1 | LLM 2 | LLM 3|
| -------- | ------- |------- |------- |
| Field 1 |     |  |  |
| Field 2 |    |  |  |
| Field 3    |     |  |  |

> [!Note]
> Control+C doesn't end ollama Terminal. Use this to end:
```shell
>>> /bye
```

🎉 **Check Point 1**


## 3. Python programming with ```Ollama```

- [ ] **Install ```Ollama Python library```**

```shell
pip3 install ollama --break-system-packages
```

Go to your Python, check if ```import ollama``` works.

- [ ] **Structured answer**

Without extra setting, LLMs generate answers in natural language, similar to daily chat.

However, in Python, working with natural language (plain text) is not ideal.
<br>It can be hard to integrate with other applications.
<br>Instead, we prefer LLM answers to be organized in a structured format.

In ```Ollama```, we can enforece the answer from daily chat format to structured JSON format.
<br> https://ollama.com/blog/structured-outputs

Here is an example:     

```python
from ollama import chat
from pydantic import BaseModel
from typing import List

class SyrNear(BaseModel):
    city_name: str
    distance: int
    feature: str

class SyrNearList(BaseModel):
    cities: List[SyrNear]

response = chat(
    messages=[
        {
            'role': 'user',
            'content': 'List some cities close to Syracuse, NY.',
        }
    ],
    model='llama3.2',
    format=SyrNearList.model_json_schema(),  # Expecting a list format
)

syr_near_cities = SyrNearList.model_validate_json(response.message.content)

print(syr_near_cities)
```

Python output is:

```shell
>>> %Run -c $EDITOR_CONTENT
cities=[SyrNear(city_name='Syracuse', distance=0, feature=''),
SyrNear(city_name='Utica', distance=35, feature='state capital'),
SyrNear(city_name='Rome', distance=41, feature='Catholic diocese'),
SyrNear(city_name='Binghamton', distance=75, feature='UNESCO World Heritage site'),
SyrNear(city_name='Oneida', distance=25, feature=''),
SyrNear(city_name='Schenectady', distance=115, feature='industrial center')]
```

For your task, pick any questions in any field you like, 
<br>try to enforce the LLM answer into a structured format.

🎉 **Check Point 2**


---
