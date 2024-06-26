# terminalbot Python Package

`terminalbot` is a Python package designed to facilitate interaction with Telegram messages, enabling the execution of commands received via messages and sending messages back to a Telegram group.

## About

`terminalbot` simplifies the integration of Telegram messaging with Python applications, providing seamless communication capabilities for executing commands and sending messages within a specified group. It leverages Telegram's API for reliable message handling and processing.

## Features

- **Message Reception**: Receive and process messages from a specified Telegram group.
- **Command Execution**: Execute commands received via Telegram messages directly from Python scripts.
- **Message Sending**: Send custom messages to a Telegram group.
- **Continuous Operation**: Support for continuous message processing using a persistent loop.

## Installation

You can install `terminalbot` using pip:

```bash
pip install terminalbot
```

## Usage Examples

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
    
    # Send a reply message with the executed command
    message_to_send = f"Executed command: {chat}"
    terminalbot.send_message(telegram_bot, telegram_group, message_to_send)
else:
    print("No new commands or messages")
```


## Acknowledgments

Special thanks to the Telegram team for providing a robust API and to the Python community for their continuous support and feedback.

## License

This project is licensed under the MIT License - see the [LICENSE](https://github.com/bytebreach/TerminalBot) file for details.
