# Ollama as API on Modal

<p align="center">
    <img src="./xei_ollama.jpg" width="512px" height="512px" />
</p>

## Serving 

```
modal serve ollama-modal.py
```

## Deployment

```
modal deploy ollama-modal.py
```

## API Interaction 

When you `serve` or `deploy` your Ollama instance to modal, you will get a link like `https://your-org-name--your-app-name-main-dev.modal.run`. This name will be appeared to you just after running one of the above commands and you can use it in curl, python code, etc. 

### Request structure 

The request is a simple JSON object like the following:

```json
{
    "messages" : [
        {
            "role" : "user",
            "content" : "What is the answer to universe, life and everything?"
        }
    ]
}
```

Remember that this API is _NOT_ OpenAI compatible, but since the result and request body is identical to OpenAI's, you may be able to make it a part of an OpenAI compatible API. 

### Sample request

```bash
curl --location --request POST 'https://your-org-name--your-app-name-main-dev.modal.run' \
--header 'Content-Type: application/json' \
--data-raw '{
    "messages" : [
        {
            "role" : "user",
            "content" : "write a joke on Elon Musk"
        }
    ]
}'
```

## Tested models (Ollama Repository IDs) and GPU's

- `hagiri/xei:0.1b` : CPU (or T4)
- `haghiri/xei:0.5b` : CPU (or T4)
- `haghiri/xei:2b` : T4
- `haghiri/xei:8b` : T4 (or A10G for better performance)
- `haghiri/xei:32b` : A100 or L40S 
- `haghiri/xei:100b` : H100 
- `haghiri/xei:671b` : H100 x 2 (or 3)