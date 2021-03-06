# Define the files we need to compile.
# Anything not in this list will not be compiled into mlpack.
set(SOURCES
  nca.hpp
  nca_impl.hpp
  nca_softmax_error_function.hpp
  nca_softmax_error_function_impl.hpp
)

# Add directory name to sources.
set(DIR_SRCS)
foreach(file ${SOURCES})
  set(DIR_SRCS ${DIR_SRCS} ${CMAKE_CURRENT_SOURCE_DIR}/${file})
endforeach()
# Append sources (with directory name) to list of all mlpack sources (used at
# the parent scope).
set(MLPACK_SRCS ${MLPACK_SRCS} ${DIR_SRCS} PARENT_SCOPE)

add_cli_executable(nca)
add_python_binding(nca)
add_markdown_docs(nca "cli;python" "transformations")
