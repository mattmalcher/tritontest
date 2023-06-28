# tritontest
Playing around setting up triton inference server, following the [quickstart](https://docs.nvidia.com/deeplearning/triton-inference-server/user-guide/docs/getting_started/quickstart.html) guide, which has files [here](https://github.com/triton-inference-server/server).


Triton versions here: https://catalog.ngc.nvidia.com/orgs/nvidia/containers/tritonserver/tags


# Steps

* set up nvidia drivers
* set up nvidia docker
* test gpu hello world image works
* Clone the inference server repo
* copy the example models folder 
    ```sh
    cp -r ../triton-server/docs/examples/ models/    
    ```
* run models script `./models/fetch_models.sh
* run triton docker, specifying models dir:
    ```sh
    docker run --gpus=1 \
    --rm \
    -p8000:8000 \
    -p8001:8001 \
    -p8002:8002 \
    -v$(pwd)/models/model_repository:/models \
    nvcr.io/nvidia/tritonserver:23.05-py3 \
    tritonserver --model-repository=/models
    ```


