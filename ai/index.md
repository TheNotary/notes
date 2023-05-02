#


## Benchmarks for AI

'helm

## LLMs

- ChatGPT (is this technically a fine-tuning ontop of various models though, GPT-3/4/etc?)
- Dolle 2.0


## Unknown Technologies

- MLFlow: track generations on different model checkpoints
- DeepSpeed (Azure)
- MosaicML Composer -
  - https://docs.wandb.ai/guides/integrations/composer#:~:text=Composer%20is%20a%20library%20for,composing%20many%20different%20enhancements%20easy.
- Hugging Face accelerate
- Instruction tuning: Method of tuning an LLM to follow instructions.
- Token Latency:
- Model Serving:
- The tweets model
- GPU, non-pythonic way,
- DoorDash Model Serving blog post
  -


###### Sliding Window of Context

- Input limited to 2048 tokens (sliding window of context).  Everytime the model generates a token, it replaces the earliest token on the input.



###### Training Tips

- Have a general enough dataset to enable overtraining
-



###### Anatomy of LLMs

-
-
-


###### Quantization

64bits is too much
16bits seems to work
lower than that, ymmv
