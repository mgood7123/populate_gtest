# populate_gtest

a git repository to populate gtest as a cmake submodule in a way that is compatible for use with submodules and stand alone compilations

## usage

in your Terminal
```shell script
git submodule add https://github.com/mgood7123/populate_gtest populate_gtest
```

in your CMakeList.txt
```cmake
add_subdirectory(populate_gtest)
```

and your done!

have a nice day :)