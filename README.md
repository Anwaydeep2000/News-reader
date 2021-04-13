# News-reader
def speak(str):
    from win32com.client import Dispatch
    speak=Dispatch("SAPI.spVoice")
    speak.Speak(str)

if __name__ == '__main__':

    import requests
    import json
    url = ('https://newsapi.org/v2/top-headlines?country=us&apiKey=a5870cb4a5f94e4595f6095d41fdafe2')

    response = requests.get(url)
    text = response.text
    my_json = json.loads(text)
    for i in range(0, 11):
        speak(my_json['articles'][i]['title'])
