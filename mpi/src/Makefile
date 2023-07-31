EXECS = mpi_hello_world \
	mpi_send_recv mpi_ping_pong mpi_ring \
	mpi_my_bcast mpi_compare_bcast \
        mpi_avg mpi_all_avg \
	mpi_reduce_avg mpi_reduce_stddev \
        mpi_random_walk 

MPICC?=mpicc
MPICXX?=mpicxx

all: ${EXECS}

mpi_hello_world: mpi_hello_world.c
	${MPICC} -o mpi_hello_world mpi_hello_world.c

mpi_send_recv: mpi_send_recv.c
	${MPICC} -o mpi_send_recv mpi_send_recv.c

mpi_ping_pong: mpi_ping_pong.c
	${MPICC} -o mpi_ping_pong mpi_ping_pong.c

mpi_ring: mpi_ring.c
	${MPICC} -o mpi_ring mpi_ring.c

mpi_random_walk: mpi_random_walk.cc
	${MPICXX} -o mpi_random_walk mpi_random_walk.cc

mpi_my_bcast: mpi_my_bcast.c
	${MPICC} -o mpi_my_bcast mpi_my_bcast.c

mpi_compare_bcast: mpi_compare_bcast.c
	${MPICC} -o mpi_compare_bcast mpi_compare_bcast.c

mpi_avg: mpi_avg.c
	${MPICC} -o mpi_avg mpi_avg.c

mpi_all_avg: mpi_all_avg.c
	${MPICC} -o mpi_all_avg mpi_all_avg.c

mpi_reduce_avg: mpi_reduce_avg.c
	${MPICC} -o mpi_reduce_avg mpi_reduce_avg.c

mpi_reduce_stddev: mpi_reduce_stddev.c
	${MPICC} -o mpi_reduce_stddev mpi_reduce_stddev.c -lm

clean:
	rm -f ${EXECS}

