# Local AI Agent from Scratch

This [notebook](./agent_from_scratch.ipynb) demonstrates how to build a simple function-calling AI agent from scratch using the OpenAI-compatible API format and a local vLLM inference server. It shows how to structure prompts, parse model outputs, and route function calls.

> **NOTE:** Before running the notebook, launch a vLLM server in a separate terminal using your model of choice: `vllm serve <model>`

I am using [Salesforce/xLAM-2-3b-fc-r](https://huggingface.co/Salesforce/xLAM-2-3b-fc-r) due to its small size and high ranking on the [Berkeley Function-Calling Leaderboard](https://gorilla.cs.berkeley.edu/leaderboard.html).  The model is running locally on my Nvidia RTX 3060.

**vLLM launch command:**
```bash
vllm serve Salesforce/xLAM-2-3b-fc-r --enable-auto-tool-choice --tool-parser-plugin ./xlam_tool_call_parser.py --tool-call-parser xlam --tensor-parallel-size 1 --dtype float16 --gpu-memory-utilization 0.8
```

The full vLLM launch instructions for this particular model can be found in the [_**Using vLLM for Inference**_ section](https://huggingface.co/Salesforce/xLAM-2-3b-fc-r#using-vllm-for-inference) on the model's HugginngFace page.
