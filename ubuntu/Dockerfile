# Base Image
FROM nvcr.io/nvidia/l4t-base:35.4.1
ENV TZ=Asia/Kolkata LC_ALL=en_US.UTF-8 LANG=en_US.UTF-8
RUN ln -snf /usr/share/zoneinfo/$TZ /etc/localtime && echo $TZ > /etc/timezone

RUN apt-get update -y 
RUN apt-get install python3-pip make g++ libopenblas-base -y 
RUN pip3 install -U pip
RUN DEBIAN_FRONTEND=noninteractive apt-get install libhdf5-serial-dev hdf5-tools libhdf5-dev zlib1g-dev zip libjpeg8-dev -y
RUN DEBIAN_FRONTEND=noninteractive apt-get install python3 python-dev python3-dev build-essential libssl-dev libffi-dev libxml2-dev libxslt1-dev zlib1g-dev -yq
RUN pip3 install -U numpy grpcio absl-py py-cpuinfo psutil portpicker six mock requests gast h5py astor termcolor protobuf keras-applications keras-preprocessing wrapt google-pasta
RUN pip3 install --pre --extra-index-url https://developer.download.nvidia.com/compute/redist/jp/v42 tensorflow-gpu

## jupyter_torchvision
RUN pip3 install jupyterlab
RUN apt update && apt -yq install npm nodejs python3-pil python3-opencv git libopenmpi-dev openmpi-bin
RUN apt update && apt -yq install python3-matplotlib
RUN git clone https://github.com/NVIDIA-AI-IOT/torch2trt.git /torch2trt && mv /torch2trt/torch2trt /usr/local/lib/python3.6/dist-packages && rm -r /torch2trt
COPY tensorrt /usr/lib/python3.6/dist-packages/tensorrt
RUN pip3 install --no-deps fastai
RUN git clone https://github.com/fastai/fastai /fastai
RUN apt update && apt install libblas3 liblapack3 liblapack-dev libblas-dev libjpeg-dev zlib1g-dev gfortran -yq
RUN pip3 install scipy 
RUN pip3 install pandas
COPY blis-0.4.0-cp36-cp36m-linux_aarch64.whl .
RUN pip3 install blis-0.4.0-cp36-cp36m-linux_aarch64.whl
RUN pip3 install spacy
RUN pip3 install fastai
RUN git clone --branch v0.5.0 https://github.com/pytorch/vision torchvision
RUN cd torchvision && python3 setup.py install
#RUN cd /fastai && pip3 install $(python3 setup.py -q deps --dep-groups=core,vision)
RUN wget https://nvidia.box.com/shared/static/ncgzus5o23uck9i5oth2n8n06k340l6k.whl -O torch-1.4.0-cp36-cp36m-linux_aarch64.whl
RUN pip3 install Cython
RUN pip3 install numpy torch-1.4.0-cp36-cp36m-linux_aarch64.whl
CMD [ "bash" ]

## aiortc 
RUN apt update && apt -yq install python3-pil python3-opencv libavdevice-dev libavfilter-dev libopus-dev libvpx-dev pkg-config python3-cffi
ENV DEBIAN_FRONTEND=noninteractive
RUN apt -yq install libffi-dev libssl-dev libsrtp2-dev
RUN pip3 install aiohttp aiortc
RUN pip3 install minio jinja2 cachetools pyyaml pyzmq watchdog[watchmedo]
RUN apt install curl git cmake ack vim-youcompleteme vim-syntastic -yq
RUN sh -c "$(curl -fsSL https://raw.githubusercontent.com/qooba/vim-python-ide/master/setup.sh)"
RUN pip3 install aiohttp_cors ujson
WORKDIR /app/
CMD ["/bin/bash"]

## fastai
RUN git clone https://github.com/NVIDIA-AI-IOT/torch2trt.git /torch2trt && mv /torch2trt/torch2trt /usr/local/lib/python3.6/dist-packages && rm -r /torch2trt
COPY tensorrt /usr/lib/python3.6/dist-packages/tensorrt
RUN pip3 install --no-deps fastai
RUN git clone https://github.com/fastai/fastai /fastai
RUN apt update && apt install libblas3 liblapack3 liblapack-dev libblas-dev gfortran -yq
RUN pip3 install scipy 
RUN pip3 install pandas
COPY blis-0.4.0-cp36-cp36m-linux_aarch64.whl .
RUN pip3 install blis-0.4.0-cp36-cp36m-linux_aarch64.whl
RUN pip3 install spacy
RUN pip3 install fastai
RUN pip3 install scikit-learn
#RUN cd /fastai && pip3 install $(python3 setup.py -q deps --dep-groups=core,vision)
CMD [ "bash" ]

