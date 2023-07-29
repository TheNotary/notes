#



## On calculating Perplexity

Ref: https://huggingface.co/docs/transformers/perplexity

### Mystery Verbs
- autoregressively factorizing a sequence and conditioning on Blah
- exponentiating the cross-entropy between the data and model predictions.

### Mystery Nouns
- cross-entropy (between data and model predictions)
- Bits Per Character (BPC)
- log-likelihood
- Perplexity (PPL),
- classical/ autoregressive/ causal language models (transformer-based models are of this kind)
- approximate models (tend to have constraints on context window?)
- sliding-window strategy: filo stack
- strided sliding-window strategy: Incrimenting the context window in steps greater than 1 unit at a time.
- forward pass


## Data Science Terms

- differentiation engine
- Autograd engine (pytorch has one)
- backpropagation (inc reverse-mode autodiff)
- Dynamically built DAG
- Vanishing Gradient Problem
- long-range dependencies
- transduction models (of kind sequence, image, graph, or set)
- Differentiation
- RMT - Recurrent Memory Transformer


## ML Libraries

- PyTorch
- scikit-learn
- TensorFlow
- auto_gptq - For local inferance on CPU/ GPU
- llama_cpp - for local inferance on CPU
-

## Model Formats and Quantization Algorithms

There are several model formats.

- GGML/ GPT-for-all / GPT4X / GPTJ
- [GPTQ](https://arxiv.org/abs/2210.17323) - A one-shot weight quantization method, that is both highly-accurate and highly-efficient. This approach doubles the compression gains relative to previously-proposed one-shot quantization methods, preserving accuracy, allowing say 175 billion-parameter models inside a single GPU for generative inference.
- fp16 (pytorch format fp16) - This abreviation, fp16 stands for floating point 16 refering to the quantized down form of the model weights (quantized down from it's initial 64ish??? bit size).  These uploads include tokenizers and have files with .pytorch in the name.  I have to imagine these are not very well finetuned for local development the way the other formats are (quantized not to 16 bits, but down to sometimes just 3 bits).


## ML Tools

- Apache TVM deep learning compiler.
- MLFlow: track generations on different model checkpoints
- DeepSpeed (Azure)
- MosaicML Composer -
  - https://docs.wandb.ai/guides/integrations/composer#:~:text=Composer%20is%20a%20library%20for,composing%20many%20different%20enhancements%20easy.
- Hugging Face accelerate



## Tasks for NNs

- Image classification: e.g. assigning a class label to an image based on its content.  (CNN)
- Object detection: identifying and locating objects within an image (CNN: R-CNN, YOLO, SSD)
- Image segmentation: partitioning an image into multiple segments, each representing a distinct object or region. (CNN: U-Net, Mask R-CNN, DeepLab)
- Natural language processing tasks (transformers: GPT, BERT)
  - text classification
  - sentiment analysis
  - named entity recognition
  - text generation, next word prediction
  - language translation
- Machine translation: translating text from one language to another.  (RNN, LSTM, GRU)
- Speech recognition: converting spoken language into written text)




## Benchmarks for AI

'helm

## LLMs

- ChatGPT (is this technically a fine-tuning ontop of various models though, GPT-3/4/etc?)
- Dolle 2.0









## Unknown Terms/ Technologies

- Instruction tuning: Method of tuning an LLM to follow instructions.
- Token Latency:
- Model Serving:
- The tweets model
- GPU, non-pythonic way,
- DoorDash Model Serving blog post
  -
- GraphGPT: https://github.com/varunshenoy/GraphGPT



## Neural Network (NN) Types

- Convolutional NN (CNN) - Good for image recognition
- Long short-term memory network (LSTM) - Good for speech recognition
- Large Lanug




###### Sliding Window of Context, vanishing gradient problem

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
