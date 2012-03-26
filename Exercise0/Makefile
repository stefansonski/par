# This Makefile is brutally simple, not very sophisticated,
# and not at all up to my normal standards...
# ...Be grateful, dear reader!
# (Signed, Prof. R. Moore, h_da, fbi )

# --------------------------------------------------------------------------
all: mpi-pi cpp11-pi openMP-pi

clean:
	-rm -f *.o mpi-pi cpp11-pi openMP-pi

mpi-pi.o: mpi-pi.c
	mpicc -c $<

mpi-pi: mpi-pi.o
	mpicc -o mpi-pi mpi-pi.o


cpp11-pi.o: cpp11-pi.cpp
	c++ -std=c++0x -pthread -c $<

cpp11-pi: cpp11-pi.o
	c++ -std=c++0x -o cpp11-pi cpp11-pi.o -lpthread

openMP-pi.o: openMP-pi.cpp
	c++ -std=c++0x -fopenmp -c $<

openMP-pi: openMP-pi.o
	c++ -std=c++0x -fopenmp -o openMP-pi openMP-pi.o

tests: all
	echo -e "\nRunning mpi-pi...";
	mpiexec -n 4 ./mpi-pi
	echo -e "\nRunning cpp11-pi...";
	./cpp11-pi 4
	echo -e "\nRunning openMP-pi...";
	./openMP-pi 4



