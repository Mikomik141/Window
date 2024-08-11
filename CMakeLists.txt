cmake_minimum_required(VERSION 3.7)
project(window)

set(CMAKE_CXX_STANDARD 14)
set(CMAKE_BUILD_TYPE Debug)

# Désactiver la construction de la documentation, des tests et des exemples de GLFW
set(GLFW_BUILD_DOCS OFF CACHE BOOL "" FORCE)
set(GLFW_BUILD_TESTS OFF CACHE BOOL "" FORCE)
set(GLFW_BUILD_EXAMPLES OFF CACHE BOOL "" FORCE)

# Ajouter les sous-répertoires pour GLFW et GLAD
add_subdirectory(/home/amale/glfw /home/amale/glfw/src)
add_subdirectory(/home/amale/glad /home/amale/glad/src)
add_subdirectory(/home/amale/linmath.h-master/ /home/amale/linmath.h-master/src)
# Trouver le package OpenGL
find_package(OpenGL REQUIRED)
find_package(glm CONFIG REQUIRED)
# Définir les fichiers sources
set(SOURCE_FILES main.cpp)

# Ajouter l'exécutable
add_executable(window ${SOURCE_FILES})

# Lier les bibliothèques
target_link_libraries(window glfw)
target_link_libraries(window OpenGL::GL)
target_link_libraries(window glad)
target_link_libraries(window linmath)
target_link_libraries(window  glm::glm)