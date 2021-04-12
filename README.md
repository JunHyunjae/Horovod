# Horovod

  멀티 GPU를 효율적으로 쓰기 위해 Horovod를 설치하는 방법을 정리함.

  1. Open MPI 설치
    https://www.open-mpi.org/software/ompi/v4.0/

    위 사이트서 압축 파일을 다운로드

    cd openmpi-4.0.1
    ./configure --prefix=/usr/local
    <...lots of output...>
    sudo make all install

    desktop@desktop:~$ mpirun
    --------------------------------------------------------------------------
    mpirun could not find anything to do.

    It is possible that you forgot to specify how many processes to run
    via the "-np" argument.
    --------------------------------------------------------------------------
    위와 같이 나오면 설치 성공

  2. NCCL 설이

    https://developer.nvidia.com/nccl 다운로드

    dpkg -i nccl~.dev
    sudo apt-get update
    sudo apt-get install libnccl2 libnccl-dev  

  3. HOROVOD 설치

    pip3 install horovod # cpu installation
    HOROVOD_GPU_OPERATIONS=NCCL pip3 install horovod # gpu installation
