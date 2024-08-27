Need to temporarily run commands in another environment?
docker run -it --rm -v $(pwd):/app ubuntu:20.04 /bin/bash