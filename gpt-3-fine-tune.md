# Finetune GTPT-3



1. First we must upload a file to open ai
2. Then we must reference that file in the fine tuning api



## Upload a file containing the finetuning

Check https://beta.openai.com/docs/api-reference/files/upload?lang=curl

```bash
curl -k https://api.openai.com/v1/files -H "Authorization: Bearer API_KEY" -F purpose="fine-tune" -F file='@FINE-TUNE-FILE.jsonl'
```

This call will return the file id. 

*Remember the special format of the finetuning file: https://beta.openai.com/docs/guides/fine-tuning/prepare-training-data*



## Finetune a model

```bash
curl -k https://api.openai.com/v1/fine-tunes -X POST -H "Content-Type: application/json" -H "Authorization: Bearer API_KEY" -d '{"training_file": "FILE_ID", "model": "MODEL_NAME"}'
```

`MODEL_NAME` could be `davinci` or `curie`



