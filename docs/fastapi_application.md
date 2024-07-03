
# Creating the FastAPI Application

In this section, you will learn how to create a FastAPI application to serve your AI model. We will provide detailed examples for different input and output types.

## Basic FastAPI Application Structure
Here is a basic structure for a FastAPI application:

```python
from fastapi import FastAPI, File, Form, UploadFile, HTTPException
from pydantic import BaseModel, ValidationError, validator
from typing import List, Optional, Dict, Union
from fastapi.responses import JSONResponse

app = FastAPI()

@app.post("/predict/")
async def predict(input_text: str = Form(...), input_image: UploadFile = File(None)):
    return {"input_text": input_text, "input_image": input_image.filename if input_image else None}
```

## Example: Text Input and Text Output
If your model accepts text as input and returns text as output, you can define your endpoint as follows:

### Input and Output Types
```json
{
  "input_types": [
    {
      "name": "input_text",
      "type": "text",
      "description": "The text input for sentiment analysis",
      "required": true
    }
  ],
  "output_types": [
    {
      "name": "output_text",
      "type": "text",
      "description": "The sentiment analysis result",
      "required": true
    }
  ]
}
```

### FastAPI Example
```python
from fastapi import FastAPI, Form
from pydantic import BaseModel

app = FastAPI()

@app.post("/predict/")
async def predict(input_text: str = Form(...)):
    # Example prediction logic
    output_text = input_text[::-1]  # Reverse the input text
    return {"output_text": output_text}
```

## Example: Image Input and Text Output
If your model accepts an image as input and returns text as output, your endpoint will look like this:

### Input and Output Types
```json
{
  "input_types": [
    {
      "name": "input_image",
      "type": "image",
      "description": "An image input for object detection",
      "required": true
    }
  ],
  "output_types": [
    {
      "name": "output_text",
      "type": "text",
      "description": "Detected objects in the image",
      "required": true
    }
  ]
}
```

### FastAPI Example
```python
from fastapi import FastAPI, File, UploadFile
from typing import List

app = FastAPI()

@app.post("/predict/")
async def predict(input_image: UploadFile = File(...)):
    # Example prediction logic
    output_text = f"Processed image {input_image.filename}"
    return {"output_text": output_text}
```

## Example: Text and Image Input, Text Output
If your model accepts both text and image as input and returns text as output, your endpoint will look like this:

### Input and Output Types
```json
{
  "input_types": [
    {
      "name": "input_text",
      "type": "text",
      "description": "The text input for context",
      "required": true
    },
    {
      "name": "input_image",
      "type": "image",
      "description": "An image input for processing",
      "required": true
    }
  ],
  "output_types": [
    {
      "name": "output_text",
      "type": "text",
      "description": "The result of processing the text and image",
      "required": true
    }
  ]
}
```

### FastAPI Example
```python
from fastapi import FastAPI, File, Form, UploadFile

app = FastAPI()

@app.post("/predict/")
async def predict(input_text: str = Form(...), input_image: UploadFile = File(...)):
    # Example prediction logic
    output_text = f"Processed text '{input_text}' and image '{input_image.filename}'"
    return {"output_text": output_text}
```

## Example: Text Input, Dictionary Output
If your model accepts text as input and returns a dictionary as output, your endpoint will look like this:

### Input and Output Types
```json
{
  "input_types": [
    {
      "name": "input_text",
      "type": "text",
      "description": "The text input for analysis",
      "required": true
    }
  ],
  "output_types": [
    {
      "name": "output_dict",
      "type": "dictionary",
      "description": "The analysis result as a dictionary",
      "required": true
    }
  ]
}
```

### FastAPI Example
```python
from fastapi import FastAPI, Form
from typing import Dict

app = FastAPI()

@app.post("/predict/")
async def predict(input_text: str = Form(...)):
    # Example prediction logic
    output_dict = {"original_text": input_text, "reversed_text": input_text[::-1]}
    return {"output_dict": output_dict}
```

## Adding Additional Functions
If your model requires additional functions, include them in separate files within the zip file. Import these functions into your `main.py`.

### Example: Including Additional Functions
1. **Create a file named `utils.py` for additional functions.**

```python
# utils.py
def reverse_text(text: str) -> str:
    return text[::-1]
```

2. **Import and use the function in `main.py`.**

```python
from fastapi import FastAPI, Form
from utils import reverse_text

app = FastAPI()

@app.post("/predict/")
async def predict(input_text: str = Form(...)):
    # Use the additional function
    output_text = reverse_text(input_text)
    return {"output_text": output_text}
```

3. **Ensure `utils.py` is included in the zip file along with `main.py`, `Dockerfile`, and `requirements.txt`.**

---

Proceed to the next section: [Packaging with Docker](packaging_with_docker.md)