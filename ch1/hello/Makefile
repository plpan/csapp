SRC=hello.c
PRE=hello.i
ASM=hello.s
OBJ=hello.o
EXE=hello

all:
	gcc -Wall -save-temps -o ${EXE} ${SRC}

build: load

build_gcc: load_gcc

# 链接
load: assembly ${OBJ} print.o
	ld -o ${EXE} $(word 2, $^) print.o -lc # 必须提供print.o对象文件，并附加-lc链接选项装在标准c库

# 链接，gcc实现
load_gcc: assembly ${OBJ}
	gcc -Wall -o ${EXE} $(word 2, $^)

# 汇编
assembly: compile ${ASM}
	gcc -Wall -c -fPIC -o ${OBJ} $(word 2, $^)

# 编译
compile: preprocess ${PRE}
	gcc -Wall -S -o ${ASM} $(word 2,$^)

# 预处理
preprocess: ${SRC}
	gcc -Wall -E -o ${PRE} $^

clean:
	rm ${PRE} ${ASM} ${OBJ} ${EXE}

.PHONY: build load assembly compile preprocess
