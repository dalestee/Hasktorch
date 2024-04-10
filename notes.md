#Dependencies for hasktorch

- Python : Version 3.9.2

- Stack  : Version 2.11.1, Git revision c1167a6abc3f4978ccded5ba0246a57387da0e2f x86_64 hpack-0.35.2

#Installing linux+cabal+cpu

- Clone the repository [hasktorch](https://github.com/hasktorch/hasktorch.git)

- Change lines that use python (because my computer has python3) at deps/get-deps.sh

- Run the following commands:
```bash
$ pushd deps       # Change to the deps directory and save the current directory.
$ ./get-deps.sh    # Run the shell script to retrieve the libtorch dependencies.
$ popd             # Go back to the root directory of the project.
$ source setenv    # Set the shell environment to reference the shared library locations.
```

- Build the project with the following commands:
```bash
$ stack build hasktorch  # Build the Hasktorch library.
$ stack test hasktorch   # Build and run the Hasktorch library test suite.
$ stack build examples  # Build the Hasktorch examples.
$ stack test examples   # Build and run the Hasktorch example test suites.
```

- Testing
```bash
$ cd examples                   # Change to the examples directory.
$ ./datasets/download-mnist.sh  # Download the MNIST dataset.
$ mv mnist data                 # Move the MNIST dataset to the data directory.
$ export DEVICE=cpu             # Set device to CPU for the MNIST CNN example.
$ stack run static-mnist-cnn    # Run the MNIST CNN example.
```