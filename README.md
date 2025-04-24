使用 nature 实现的 Llama2 model，这是从 [llama2.c](https://github.com/karpathy/llama2.c) 移植而来。由于 nature 没有进行 SIMD 优化，所以只有 llama2.c 1/4 左右的性能。

## 构建

1. install the https://github.com/nature-lang/nature nature compiler
2. `nature build main.n` 获取 main 可执行文件
3. 运行 `./main` 查看运行程序使用方式

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

4. 拉取 stories15M.bin 模型到当前目录进行测试 

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