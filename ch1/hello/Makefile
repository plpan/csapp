SRC=hello.c
PRE=hello.i
ASM=hello.s
OBJ=hello.o
EXE=hello

build: load

build_gcc: load_gcc

# 链接
load: assembly ${OBJ} print.o
	ld -o ${EXE} $(word 2, $^) print.o -lc # 必须提供print.o对象文件，并附加-lc链接选项装在标准c库

# 链接，gcc实现
load_gcc: assembly ${OBJ}
	gcc -o ${EXE} $(word 2, $^)

# 汇编
assembly: compile ${ASM}
	gcc -c -fPIC -o ${OBJ} $(word 2, $^)

# 编译
compile: preprocess ${PRE}
	gcc -S -o ${ASM} $(word 2,$^)

# 预处理
preprocess: ${SRC}
	gcc -E -o ${PRE} $^

clean:
	rm ${PRE} ${ASM} ${OBJ} ${EXE}

.PHONY: build load assembly compile preprocess
