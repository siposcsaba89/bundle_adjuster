cmake_minimum_required(VERSION 3.0)

project(bundle_adjuster)

find_package(glog REQUIRED)
find_package(gflags REQUIRED)
set(SuiteSparse_USE_LAPACK_BLAS ON)
find_package(SuiteSparse REQUIRED)
include(${USE_SuiteSparse})

find_package(ceres REQUIRED CONFIG)

add_executable(bundle_adjuster bundle_adjuster.cc bal_problem.h bal_problem.cc)
#message(FATAL_ERROR ${CERES_INCLUDE_DIRS})
target_include_directories(bundle_adjuster PRIVATE ${CERES_INCLUDE_DIRS})
target_link_libraries(bundle_adjuster ceres)
