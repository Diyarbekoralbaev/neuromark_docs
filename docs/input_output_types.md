
# Defining Input and Output Types

Defining the input and output types for your AI model is a crucial step. This helps users understand how to interact with your model.

## Input Types
Input types specify the data your model accepts. Each input type should have a name, type, description, and a flag indicating if it is required.

### Example
Here is an example of how to define input types in JSON format:

```json
{
  "input_types": [
    {
      "name": "input_text",
      "type": "text",
      "description": "An input text",
      "required": true
    },
    {
      "name": "input_image",
      "type": "image",
      "description": "An input image",
      "required": false
    }
  ]
}
```

### Detailed Examples
- **Text Input**
  ```json
  {
    "name": "input_text",
    "type": "text",
    "description": "The text input for sentiment analysis",
    "required": true
  }
  ```
  - **Name:** input_text
  - **Type:** text
  - **Description:** The text input for sentiment analysis.
  - **Required:** true

- **Image Input**
  ```json
  {
    "name": "input_image",
    "type": "image",
    "description": "An image input for object detection",
    "required": false
  }
  ```
  - **Name:** input_image
  - **Type:** image
  - **Description:** An image input for object detection.
  - **Required:** false

- **Integer Input**
  ```json
  {
    "name": "input_number",
    "type": "integer",
    "description": "An integer input for numerical prediction",
    "required": true
  }
  ```
  - **Name:** input_number
  - **Type:** integer
  - **Description:** An integer input for numerical prediction.
  - **Required:** true

- **Boolean Input**
  ```json
  {
    "name": "input_flag",
    "type": "boolean",
    "description": "A boolean input for binary classification",
    "required": false
  }
  ```
  - **Name:** input_flag
  - **Type:** boolean
  - **Description:** A boolean input for binary classification.
  - **Required:** false

## Output Types
Output types specify the data your model returns. Similar to input types, each output type should have a name, type, description, and a flag indicating if it is required.

### Example
Here is an example of how to define output types in JSON format:

```json
{
  "output_types": [
    {
      "name": "output_text",
      "type": "text",
      "description": "The processed text output",
      "required": true
    }
  ]
}
```

### Detailed Examples
- **Text Output**
  ```json
  {
    "name": "output_text",
    "type": "text",
    "description": "The text output from the sentiment analysis",
    "required": true
  }
  ```
  - **Name:** output_text
  - **Type:** text
  - **Description:** The text output from the sentiment analysis.
  - **Required:** true

- **Image Output**
  ```json
  {
    "name": "output_image",
    "type": "image",
    "description": "The processed image with detected objects",
    "required": true
  }
  ```
  - **Name:** output_image
  - **Type:** image
  - **Description:** The processed image with detected objects.
  - **Required:** true

- **Float Output**
  ```json
  {
    "name": "output_score",
    "type": "float",
    "description": "The confidence score of the prediction",
    "required": true
  }
  ```
  - **Name:** output_score
  - **Type:** float
  - **Description:** The confidence score of the prediction.
  - **Required:** true

- **Dictionary Output**
  ```json
  {
    "name": "output_dict",
    "type": "dictionary",
    "description": "A dictionary containing multiple outputs",
    "required": true
  }
  ```
  - **Name:** output_dict
  - **Type:** dictionary
  - **Description:** A dictionary containing multiple outputs.
  - **Required:** true

## Complete Example
Here is a complete example that includes both input and output types:

```json
{
  "input_types": [
    {
      "name": "input_text",
      "type": "text",
      "description": "An input text",
      "required": true
    },
    {
      "name": "input_image",
      "type": "image",
      "description": "An input image",
      "required": false
    }
  ],
  "output_types": [
    {
      "name": "output_text",
      "type": "text",
      "description": "The processed text output",
      "required": true
    }
  ]
}
```

---

Proceed to the next section: [Creating the FastAPI Application](fastapi_application.md)