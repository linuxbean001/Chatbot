# Instructions for use

![](https://pic.liuzaoqi.com/picgo/202212091444750.png)

ChatGPT_PyBot is a command-line robot developed based on Python.

To use `ChatGPT_PyBot`, **you need to have an openai account, and do it on a machine that can normally log in to `ChatGPT` web version**.

## Install

`ChatGPT_PyBot` has been uploaded to `Pypi`, you can execute the following code in the terminal to install

```shell
pip install ChatGPT_PyBot --upgrade
```

Or you can also install via GitHub

```shell
pip install git+https://github.com/liuhuanshuo/ChatGPT_PyBot
```


## Configuration (very important)

After the installation is complete, you need to configure the login file. `ChatGPT_PyBot` provides two methods for login verification.

### Use account password

Create a new `config.json` file in the current directory with the following content:

```json
{
    "email":"<EMAIL>",
    "password": "<PASSWORD>"
}
```

Just fill in your account password.

Note: If you use an account password in an area not supported by `openai`, you need to configure the terminal to use proxy traffic, otherwise it will fail to verify.

You can use the following code to check the ip address of your terminal to ensure that the ip of the terminal belongs to the available area

```shell
curl cip.cc
```

### Using Cookies

If the above configuration scheme does not work, you can use the second method at this time, don't worry, it is not difficult at all.

First you need to log in to ChatGPT, and press F12 or right button - check

![](https://pic.liuzaoqi.com/picgo/202212091104801.png)

Click `Application`

![](https://pic.liuzaoqi.com/picgo/202212091105819.png)

Copy the `Cookie Value` as instructed below

![](https://pic.liuzaoqi.com/picgo/202212091107424.png)

Similarly, create a `config.json` file in the current directory with the following content:

```json
{
    "session_token":"Your Cookie Value"
}
```


## CLI usage



Open the terminal (command line), make sure there is a configured `config.json` file in the current directory, execute `chatgpt` to enter the interactive dialog

```shell
$ chatgpt
```

![](https://pic.liuzaoqi.com/picgo/202212091115468.png)

If you only need a single question, you can add your question directly after `chatgpt`


```shell
$ chatgpt your question
```

![](https://pic.liuzaoqi.com/picgo/202212091119492.png)


## Python usage


If you need to call ChatGPT in Python, you can execute the following code similarly


```python
>>> from ChatGPT_PyBot import ChatBot
>>> config = {
    "session_token":"Your token"
    				or
    "email": "<YOUR_EMAIL>",
    "password": "<YOUR_PASSWORD>"
}
>>> chatbot = ChatBot(config, conversation_id=None)
>>> chatbot.get_chat_response('hello world')["message"]


'''
"Hello there! It's nice to meet you. Is there anything I can help you with today? I'm here to answer any questions you might have."
'''
```

## Upcoming

- [ ] better way to log in (the current one is a bit cumbersome, but it is very difficult)
- [ ] refresh dialog, reset dialog



## Acknowledgments

This project is inspired by [ChatGPT - a reverse engineering of OpenAI](https://github.com/acheong08/ChatGPT).