I have to document how to build the hello world kernel example and
add that to the Makefile.

I followed these steps: https://popovicu.com/posts/bare-metal-programming-risc-v/

And the extract the text section from the kernel elf binary:

objcopy -O binary kernel.elf kernel.bin
