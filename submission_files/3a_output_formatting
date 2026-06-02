import requests
import json

def emotion_detector(text_to_analyze):
    url = 'https://sn-watson-emotion.labs.skills.network/v1/watson.runtime.nlp.v1/NlpService/EmotionPredict'
    headers = {"grpc-metadata-mm-model-id": "emotion_aggregated-workflow_lang_en_stock"}
    input = { "raw_document": { "text": text_to_analyze } }
    response = requests.post(url, json=input, headers=headers)
    response_json = json.loads(response.text)
    formatted_response = response_json['emotionPredictions'][0]['emotion']
    formatted_response['dominant_emotion'] = max(formatted_response, key=formatted_response.get)
    return formatted_response