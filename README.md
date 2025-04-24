Llama2 model implemented by nature, which is ported from [llama2.c](https://github.com/karpathy/llama2.c). Since nature is not SIMD-optimized, it has only about 1/4 of the performance of llama2.c.

## Build

1. install the https://github.com/nature-lang/nature nature compiler
2. `nature build main.n` to get the main executable.
3. Run `./main` to see how the running program works

     ```sh
    ./main
    Usage:   run <checkpoint> [options]
    Example: run model.bin -n 256 -i "Once upon a time"
    Options:
    -t <float>  temperature in [0,inf], default 1.0
    -p <float>  p value in top-p (nucleus) sampling in [0,1] default 0.9
    -s <int>    random seed, default time(NULL)
    -n <int>    number of steps to run for, default 256. 0 = max_seq_len
    -i <string> input prompt
    -z <string> optional path to custom tokenizer
    -m <string> mode: generate|chat, default: generate
    -y <string> (optional) system prompt in chat mode
    ```

4. Pull the stories15M.bin model into the current directory for testing.
    `wget https://huggingface.co/karpathy/tinyllamas/resolve/main/stories15M.bin`

5. `./main stories15M.bin -i "Once upon a time"`

    ```sh
    ./main stories15M.bin -i "Once upon a time"
    Once upon a time, there was a happy little girl named Lily. She loved to walk in the park with her mommy. One day, they saw a big dog that made them feel nervous. "Mommy, what is that?" asked Lily. "That's a big dog, Lily. He's scary," replied her mommy. 
    Lily wanted to make sure the dog was friendly, so she asked her mommy if she could pet him. Her mommy said yes, so Lily slowly walked up to the dog and pet him gently. The dog was so soft and friendly, and Lily felt very happy. 
    After a while, they continued their walk and Lily started to feel more relaxed. "Mommy, I feel better now. Can we walk again?" asked Lily. "Of course, Lily. Let's walk slowly and safely," said her mommy. And so, they walked back home, feeling happy and relaxed.
    achieved tok/s: 58.190843
    ```

## License
MIT
