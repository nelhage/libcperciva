.POSIX:

all:	test_getopt

test:	all
	@echo -n "Testing command-line options parsing... "
	@/bin/sh -e test_getopt.sh 2>test_getopt.log
	@if cmp -s test_getopt.log test_getopt.good; then	\
		echo "PASSED!";					\
	else							\
		echo "FAILED!";					\
	fi

test_getopt:	main.o getopt.o
	${CC} -o test_getopt main.o getopt.o

main.o:	main.c
	${CC} -D_POSIX_C_SOURCE=200809L -I ../../util -c main.c -o main.o

getopt.o:	../../util/getopt.c
	${CC} -D_POSIX_C_SOURCE=200809L -I ../../util -c ../../util/getopt.c -o getopt.o

clean:
	rm -f test_getopt
	rm -f main.o getopt.o
	rm -f test_getopt.log

