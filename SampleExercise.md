# Exercise: Professional and Empathetic Email Response

# Context
Email responses are crucial for maintaining customer satisfaction, especially when addressing issues like delayed shipments. In this exercise, you'll use OpenAI's completion model to craft a professional and empathetic email response to a customer inquiry about a delayed shipment. This task will showcase the model's ability to understand context and generate appropriate responses.

# Instructions
- Assign your OpenAI API key to `api_key`.
- Create a request to the Completions endpoint using the given prompt, targeting the `text-davinci-003` model with parameters `temperature=0.7`, `max_tokens=150`, `top_p=1.0`, `frequency_penalty=0.0`, and `presence_penalty=0.0`.
- Extract and print the text response from the API.

# Hint
- Use `openai.Completion.create()` to make your request to the OpenAI API.
- To get the response text, access the `.choices` list from the response, select the first element, and then retrieve the `.text` attribute.

# Sample Code
```python
# Import OpenAI library
import openai

# Set your API key
openai.api_key = "____"

# Define the prompt
prompt = """A customer has sent the following message: 
'I'm reaching out to inquire about the status of my shipment, order #12345, 
which was supposed to arrive last week but has not yet been delivered. 
Can you please update me on the current status and expected delivery date?'

Write a professional and empathetic email response to this customer inquiring about their delayed shipment:"""

# Create a request to the Completions endpoint
response = openai.Completion.create(
  engine="____",  # Model name
  prompt=____,  # Prompt variable
  temperature=____,  # Set creativity
  max_tokens=____,  # Limit response length
  top_p=____,  # Control randomness
  frequency_penalty=____,  # Reduce repetition
  presence_penalty=____  # Encourage new concepts
)

# Extract and print the response text
print(____)
```

# Solution
```python
# Import OpenAI library
import openai

# Set your API key
openai.api_key = "<YOUR_API_KEY>"

# Define the prompt
prompt = """A customer has sent the following message: 
'I'm reaching out to inquire about the status of my shipment, order #12345, 
which was supposed to arrive last week but has not yet been delivered. 
Can you please update me on the current status and expected delivery date?'

Write a professional and empathetic email response to this customer inquiring about their delayed shipment:"""

# Create a request to the Completions endpoint
response = openai.Completion.create(
  engine="text-davinci-003",
  prompt=prompt,
  temperature=0.7,
  max_tokens=150,
  top_p=1.0,
  frequency_penalty=0.0,
  presence_penalty=0.0
)

# Extract and print the response text
print(response.choices[0].text)
```
# Submission Correctness Tests (SCT)
```python
Ex().multi(
  check_object("openai.api_key"),
  check_function("openai.Completion.create").multi(
    check_args("engine").has_equal_ast(),
    check_args("prompt").has_equal_value(override=prompt),
    check_args("temperature").has_equal_value(),
    check_args("max_tokens").has_equal_value(),
    check_args("top_p").has_equal_value(),
    check_args("frequency_penalty").has_equal_value(),
    check_args("presence_penalty").has_equal_value()
  ),
  check_function("print").check_args(0).has_code("response\.choices\[\s*0\s*\]\.text", not_typed_msg="Did you extract the text from the `response`?")
)

success_msg("Great job! Crafting a professional and empathetic response is key to maintaining customer trust, especially in situations like delayed shipments. With AI, you can ensure that responses are not only quick but also considerate.")
```
