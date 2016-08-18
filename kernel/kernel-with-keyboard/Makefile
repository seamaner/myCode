CFLAGS  := -m32 -fno-stack-protector -fno-builtin -nostdinc -O -g -Wall -I.
LDFLAGS := -nostdlib -Wl,-N -Wl,-Ttext -Wl,100000

all:	kernel

kernel:	kasm.o	kc.o
	ld -m elf_i386 -T link.ld -o kernel kasm.o kc.o
	@echo Done!

kasm.o: kernel.asm
	nasm  -f elf32 -o kasm.o kernel.asm

kc.o: kernel.c keyboard_map.h
	gcc -m32 -c kernel.c -o kc.o

clean: 
	rm -f *.o *.bin
