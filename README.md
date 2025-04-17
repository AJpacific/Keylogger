# 🔐 Keystroke Logger with Periodic Data Upload

This Python script uses the `pynput` library to monitor and log keyboard input. Captured keystrokes are sent to a remote server at regular intervals via HTTP POST requests in JSON format.

⚠️ **Disclaimer**: This script demonstrates how to capture keyboard input and send it to a remote server. **Use responsibly and ethically.** Unauthorized use of keyloggers is illegal and a violation of privacy laws.

---

## 🧰 Features

- Captures all keyboard input, including special characters like `Enter`, `Tab`, and `Backspace`.
- Sends captured keystrokes as JSON payloads to a server at fixed intervals.
- Uses Python’s `threading` to run scheduled tasks in the background.
- Lightweight and easy to deploy.

---

## 📦 Requirements

- Python 3.x
- [`pynput`](https://pypi.org/project/pynput/)
- [`requests`](https://pypi.org/project/requests/)

### Install Dependencies

```bash
pip install pynput requests
```

---

## 🛠️ Configuration

Set the following variables in the script:

```python
ip_address = "109.74.200.23"  # Replace with your server IP
port_number = "8080"          # Replace with your server port
time_interval = 10            # Interval in seconds between each POST request
```

---

## 🚀 How It Works

1. **Start Listening:**  
   The script starts a `keyboard.Listener` that logs keys as they're pressed.

2. **Build Keystroke String:**  
   Keystrokes are appended to a global string variable `text`.

3. **Post to Server:**  
   Every `time_interval` seconds, a `POST` request with JSON data is sent to the configured server:
   
   ```json
   {
     "keyboardData": "user_input_here"
   }
   ```

4. **Repeat:**  
   The `send_post_req()` function schedules itself to run repeatedly using `threading.Timer`.

---

## 📄 Example Output

Here is an example of the JSON payload sent to the server:

```json
{
  "keyboardData": "hello world\nthis is a test"
}
```

---

## 🧪 Running the Script

To run the script, simply execute it with Python:

```bash
python keylogger.py
```

---

## 🛑 Exit Mechanism

Press the **Esc** key to stop the keylogger and exit the program.

---

## 🔒 Legal Note

This code is provided for educational purposes **only**. Logging keyboard input from users without their explicit consent is illegal and unethical. Make sure you have permission before running this software on any machine.

---

## 📚 Resources

- [pynput documentation](https://pynput.readthedocs.io/en/latest/)
- [requests documentation](https://requests.readthedocs.io/en/latest/)
- [Python threading](https://docs.python.org/3/library/threading.html)
