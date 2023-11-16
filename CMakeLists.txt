cmake_minimum_required(VERSION 3.10)  # Use la misma versión mínima que el primero

project(SR)  # Mantener el nombre del proyecto simple sin versión
set(CMAKE_CXX_STANDARD 20)
set(CMAKE_CXX_STANDARD_REQUIRED True)

set(CMAKE_BUILD_TYPE Release)  # Asegurarse de que se configure para lanzamiento

# Añadir las banderas de perfilado
set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -pg")

# Utilizar file(GLOB ...) para encontrar todos los archivos .cpp
file(GLOB SOURCE_FILES ${PROJECT_SOURCE_DIR}/src/*.cpp)

add_executable(SR ${SOURCE_FILES})  # Use la variable SOURCE_FILES para los archivos fuente

# Configuración de SDL2 y GLM
find_package(SDL2 REQUIRED)
include_directories(${SDL2_INCLUDE_DIRS})
include_directories(/opt/homebrew/Cellar/glm/0.9.9.8/include)

target_link_libraries(SR ${SDL2_LIBRARIES})  # Enlazar con las bibliotecas SDL2

# Las siguientes líneas parecen ser específicas para GLM y no están presentes en el primer CMakeLists.txt, pero se incluyen por coherencia
find_package(glm REQUIRED)
include_directories(${GLM_INCLUDE_DIRS})
target_link_libraries(SR ${GLM_LIBRARIES})  # Enlazar con las bibliotecas GLM
