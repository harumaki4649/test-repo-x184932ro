# TEST
Example Key Logger
```py
from pynput import keyboard

def on_press(key):
    try:
        # 押されたキーを出力
        print(f'アルファベット入力: {key.char}')
    except AttributeError:
        # 特殊キー（EnterやShiftなど）の場合
        print(f'特殊キー入力: {key}')

# キーボードの監視を開始
with keyboard.Listener(on_press=on_press) as listener:
    listener.join()
```
