# TerminalBot 2.0.0

TerminalBot is a powerful and easy-to-use Python package for interacting with Telegram groups. Whether you need to automate message sending, receive and process messages, or create complex workflows, TerminalBot provides a simple and effective solution.

## Introduction

Welcome to TerminalBot! If you've ever wished for an easier way to manage your interactions with Telegram groups, you've come to the right place. TerminalBot is designed with simplicity and efficiency in mind, making it the perfect tool for both beginners and advanced users. 
Imagine being able to automate repetitive tasks, send notifications, and interact with your Telegram community seamlessly from your terminal or Python scripts. With TerminalBot, you can do all this and more, without the hassle of complex setups or tedious coding. 
Our goal is to empower you with a tool that simplifies your workflow, saves you time, and enhances your productivity. TerminalBot leverages the full capabilities of the Telegram Bot API, providing a robust and reliable interface for your needs. Whether you're a developer looking to integrate Telegram into your applications, or a power user seeking to streamline your group management, TerminalBot has you covered.

## Features

- **Easy Installation**: Quickly install TerminalBot using pip.
- **Simple API**: Easy-to-use functions for sending and receiving messages.
- **Command Line Interface**: Convenient CLI for quick operations without writing code.
- **State Tracking**: Automatically tracks the last processed message to avoid duplicates.
- **Configurable**: Easily configure your bot with a JSON file for persistent state management.

## Benefits

- **Automation**: Automate your workflows by integrating TerminalBot with other systems.
- **Efficiency**: Save time by handling repetitive tasks through automated messaging.
- **Reliability**: Ensure messages are only processed once with state tracking.
- **Flexibility**: Use TerminalBot in your Python scripts or from the command line.
- **Scalability**: Scale your operations by leveraging the power of Telegram bots for large groups.

## Why Use TerminalBot?

- **Simplicity**: With a straightforward API and CLI, TerminalBot is easy to use even for beginners.
- **Versatility**: Suitable for various use cases, including notifications, alerts, customer support, and more.
- **Integration**: Seamlessly integrate with other Python packages and tools to build comprehensive solutions.
- **Community Support**: Join a growing community of users who leverage TerminalBot for their projects.

## Telegram API Support

TerminalBot fully supports all types and methods of the Telegram Bot API 7.4, allowing you to utilize the full capabilities of the Telegram platform. This includes sending and receiving messages, managing groups and channels, handling multimedia content, and more.

## Installation

You can install `terminalbot` using pip:

```bash
pip install terminalbot
```

## Usage Examples

### Using TerminalBot from the Command Line
### Receive a message

```bash
message=$(terminalbot --token "token" --id "@username")
echo "message is : $message"
```
- Replace <token> with your bot token and <username> with your group chat ID.

#### Receive and automatically send a response
```bash
message=$(terminalbot --token "token" --id "@username" --message-receive "Your message received")
echo "message is: $message"
```
- This command will automatically send the specified response message after receiving a message.

#### Send a message
```bash
terminalbot --token "token" --id "@username" --message "Hello world"
echo "Your message sent to the Telegram group"
```
- This command will automatically send the specified message to the Telegram group.

### 1. Receiving Messages

```python
import terminalbot

telegram_group = '@username'
telegram_bot = 'YOUR_BOT_TOKEN_HERE'

# Get the latest message
chat = terminalbot.get_message(telegram_bot, telegram_group)
if chat:
    print(f"Message received: {chat}")
else:
    print("No new messages")
```

### 2. Sending Messages

```python
import terminalbot

telegram_group = '@username'
telegram_bot = 'YOUR_BOT_TOKEN_HERE'

# Send a message
message_to_send = "Hello from terminalbot!"
terminalbot.send_message(telegram_bot, telegram_group, message_to_send)
print(f"Sent message: {message_to_send}")
```

### 3. Receiving and Executing Commands

```python
import terminalbot
import os

telegram_group = '@username'
telegram_bot = 'YOUR_BOT_TOKEN_HERE'

# Get the latest message and execute it as a command
chat = terminalbot.get_message(telegram_bot, telegram_group)
if chat:
    print(f"Executing command: {chat}")
    os.system(chat)
else:
    print("No new commands")
```

### 4. Handling Continuous Loop with Message Processing

```python
import terminalbot
import time

telegram_group = '@username'
telegram_bot = 'YOUR_BOT_TOKEN_HERE'

def main_loop(bot_token, group_chat_id):
    bot = terminalbot.TelegramBot(bot_token, group_chat_id)
    
    while True:
        message = bot.get_message()
        if message:
            print(f"Message received: {message}")
            if message.lower() == "stop terminalbot":
                print("Stopping bot.")
                break
            os.system(message)  # Example: Execute a command received via message
            print(f"Executed command: {message}")
        time.sleep(1)

if __name__ == '__main__':
    main_loop(telegram_bot, telegram_group)
```

### 5. Receiving Messages and Sending Replies

```python
import terminalbot
import os

telegram_group = '@username'
telegram_bot = 'YOUR_BOT_TOKEN_HERE'

# Get the latest message
chat = terminalbot.get_message(telegram_bot, telegram_group)
if chat:
    # Execute the received command
    os.system(chat)
    print(f"Message received: {chat}")
    
    # Send a reply message with the executed command
    message_to_send = f"Executed command: {chat}"
    terminalbot.send_message(telegram_bot, telegram_group, message_to_send)
else:
    print("No new commands or messages")
```
- For more projects, please visit our site : <a href="https://mrfidal.in/cyber-security/terminalbot/projects">Link</a>

## Thank You

Thank you for using TerminalBot! We hope this package makes your interaction with Telegram groups easier and more efficient. If you have any suggestions or feature requests, please don't hesitate to reach out.
