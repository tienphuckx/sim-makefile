
build: main.o my_lib.o
	g++ main.o my_lib.o -o main

main.o:
	g++ -c main.cc

my_lib.o:
	g++ -c my_lib.cc

run:
	./main

clean:
	rm -f *.o main
