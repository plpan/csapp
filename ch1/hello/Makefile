SRC=hello.c
PRE=hello.i
ASM=hello.s
OBJ=hello.o
EXE=hello

build: load

# 链接
load: assembly ${OBJ}
	gcc -o ${EXE} $(word 2, $^)

# 汇编
assembly: compile ${ASM}
	gcc -c -o ${OBJ} $(word 2, $^)

# 编译
compile: preprocess ${PRE}
	gcc -S -o ${ASM} $(word 2,$^)

# 预处理
preprocess: ${SRC}
	gcc -E -o ${PRE} $^

clean:
	rm ${PRE} ${ASM} ${OBJ} ${EXE}

.PHONY: build load assembly compile preprocess
