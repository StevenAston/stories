## Python Default
### Request
```
import os
from openai import OpenAI

client = OpenAI(
    api_key=os.environ.get("MIMO_API_KEY"),
    base_url="https://api.xiaomimimo.com/v1"
)

completion = client.chat.completions.create(
    model="mimo-v2-flash",
    messages=[
        {
            "role": "system",
            "content": "You are MiMo, an AI assistant developed by Xiaomi. Today is date: Tuesday, December 16, 2025. Your knowledge cutoff date is December 2024."
        },
        {
            "role": "user",
            "content": "please introduce yourself"
        }
    ],
    max_completion_tokens=1024,
    temperature=0.3,
    top_p=0.95,
    stream=False,
    stop=None,
    frequency_penalty=0,
    presence_penalty=0,
    extra_body={
        "thinking": {"type": "disabled"}
    }
)

print(completion.model_dump_json())
```
### Response
```
{
    "id": "72c2d792ca96489abd0b287184dac960",
    "choices": [
        {
            "finish_reason": "stop",
            "index": 0,
            "message": {
                "content": "Hello! I'm MiMo, a large language model developed by Xiaomi's LLM Core Team. I'm here to help you with a wide range of tasks, from answering questions and having conversations to assisting with creative writing, analysis, and problem-solving.\n\nI'm designed to be helpful, reliable, and engaging. Whether you need information, want to brainstorm ideas, or just feel like having a chat, I'm ready to assist. I try to provide clear, thoughtful responses while being mindful of context and your specific needs.\n\nWhat brings you here today? I'd love to help with whatever you're working on or curious about!",
                "role": "assistant",
                "tool_calls": null,
                "reasoning_content": null
            }
        }
    ],
    "created": 1766041014,
    "model": "mimo-v2-flash",
    "object": "chat.completion",
    "usage": {
        "completion_tokens": 127,
        "prompt_tokens": 57,
        "total_tokens": 184,
        "completion_tokens_details": {
            "reasoning_tokens": 0
        },
        "prompt_tokens_details": null
    }
}
```
