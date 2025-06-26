cmake_minimum_required(VERSION 3.12 FATAL_ERROR)

# Define a project.
project(UR_GAZEBO_MODELS LANGUAGES NONE)

# Find dependencies.
find_package(YCM 0.11 REQUIRED)
find_package(YARP 3.11 REQUIRED)

# Configure installation paths for YARP resources.
yarp_configure_external_installation(ur-gazebo-models WITH_PLUGINS)

# Install models and environments.
install(DIRECTORY models worlds
        DESTINATION share/gazebo)

add_subdirectory(share)

# Store the package in the user registry.
set(CMAKE_EXPORT_PACKAGE_REGISTRY ON)

# Create and install config files.
include(InstallBasicPackageFiles)

install_basic_package_files(UR_GAZEBO_MODELS
                            VERSION 0.1.0
                            COMPATIBILITY AnyNewerVersion
                            NO_EXPORT)

# Add uninstall rule.
include(AddUninstallTarget)
