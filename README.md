## lab07
### №1
```
mkdir lab07
cd lab07
```
### №2
```
nano Dockerfile

FROM ubuntu:18.04 
RUN apt update 
RUN apt install -yy gcc g++ cmake 
RUN mkdir hello_world 
COPY . hello_world/ 
WORKDIR hello_world 
RUN cmake -H. -B_build -DCMAKE_BUILD_TYPE=Release -DCMAKE_INSTALL_PREFIX=_install 
RUN cmake --build _build 
RUN cmake --build _build --target install 
#ENTRYPOINT ./_build/hello_world_app 
```
### №3
```
nano hello_world.cpp

#include <iostream> 
 
int main() { 
std::cout << "Hello world" << std::endl; 
}
```
### №4
```
nano CMakeLists.txt

cmake_minimum_required(VERSION 3.2) 
 
project (project_hw) 
 
add_executable(hello_world_app 
    hello_world.cpp 
) 
 
install(TARGETS hello_world_app hello_world_app RUNTIME DESTINATION /bin)
```
### №5
```
docker build -t test .
docker run test
```
