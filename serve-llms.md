
GPU ids
```
nvidia-smi --query-gpu=index,uuid --format=csv,noheader
```


docker compose file
```
services:
  vllm:
    image: vllm/vllm-openai:v0.6.2
    deploy:
      resources:
        reservations:
          devices:
          - driver: nvidia
            device_ids:
            - GPU-38dadfe7-2168-714e-be9f-dc129d7d5487
            capabilities:
            - gpu
    volumes:
    - /mnt/disk2/arshia.yousefinezhad/speed-test-local-llms/final_Llama3_part/:/Dorna
    ports:
    - 18000:8000
    ipc: host

    command: --model /Dorna/ --dtype half --tensor-parallel-size 1 --device auto --max-model-len 8192 --served-model-name Dorna
```

Take inference from local LLMs
```
client = OpenAI(
    api_key="dummy_key",
    base_url="http://localhost:18000/v1"
)

chat_completion = client.chat.completions.create(
    model="Dorna",
    messages=[{"role": "user", "content": "Hello world"}]
)
```