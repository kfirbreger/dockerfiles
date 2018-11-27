## Protoc

Generate langauge specific implemntation from a protobuf file

### Usage

Build the docker

    docker build --tag=protoc .

The folder with the protobuf file needs to be mounted into the docker. Example of generating python code from a file called envelop.proto that is in the same directory as the Dockerfile

    docker run --rm -v $(pwd):/data protoc -I=/data --python_out=/data /data/envelope.proto

In the current direcotry the protobuf python file will be availble
