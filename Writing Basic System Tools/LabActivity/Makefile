# Setup a variable to reference the desired compiler
CC = gcc

# Setup a variable to hold desired compiler flags
CFLAGS = -Wall -Wextra -Wpointer-arith -Wstrict-prototypes -std=c99 -g

# Declaring the build, test and clean rules as phony means that no artifact
#   is created by these rules with a cooresponding name.  Therefore, the
#   rule should run when executed.
.PHONY: build test clean

# The build rule depends upon the myprog artifact existing.  If it does not, make
#   will look for a rule to create it.
build: mycat mygrep mysort mywc


mycat: mycat.o
	$(CC) $(CFLAGS) $^ -o $@ 

memtest-mycat: mycat
	valgrind --tool=memcheck --leak-check=yes --show-reachable=yes ./mycat -f /usr/share/dict/american-english > /dev/null

mygrep: mygrep.o
	$(CC) $(CFLAGS) $^ -o $@ 

memtest-mygrep: mygrep
	valgrind --tool=memcheck --leak-check=yes --show-reachable=yes ./mygrep -f /usr/share/dict/american-english -s tree > /dev/null

mysort: mysort.o
	$(CC) $(CFLAGS) $^ -o $@ 

memtest-mysort: mysort
	valgrind --tool=memcheck --leak-check=yes --show-reachable=yes ./mysort -f /usr/share/dict/american-english -r > /dev/null

mywc: mywc.o
	$(CC) $(CFLAGS) $^ -o $@ 

memtest-mywc: mywc
	valgrind --tool=memcheck --leak-check=yes --show-reachable=yes ./mywc -f /usr/share/dict/american-english > /dev/null


clean:
	rm -f *.o *.d a.out mycat mygrep mysort mywc
