# CSE 030 · Data Structures

**UC Merced · Fall 2022 · C++ coursework**

An archive of lab exercises and a lecture example covering array and linked lists, templates, stacks, queues, sorting, searching, hashing, and binary search trees. Each exercise is a separate C++ project with its own headers, `main.cpp`, `test.cpp`, and Makefile.

## Explore the coursework

| Folder | Contents |
| --- | --- |
| [Lab 1](lab-1/) | [Hello World](lab-1/hello-world/) and [Hello UC Merced](lab-1/hello-ucm/) programs and output tests |
| [Lab 2](lab-2/exercise-1/) | Wordle feedback filtering in `WordleHelper.h`, with allowed-word and answer lists |
| [Lab 3](lab-3/) | [Array list](lab-3/exercise-1/), [linked list](lab-3/exercise-2/), and [abstract list / factory](lab-3/exercise-3/) exercises |
| [Lab 4](lab-4/) | Indexed access and insertion for [array](lab-4/exercise-1/) and [linked](lab-4/exercise-2/) lists |
| [Lab 5](lab-5/) | [Templated array list](lab-5/exercise-1/), [stack-based arithmetic with undo](lab-5/exercise-2/), and [queue-based round-robin scheduling](lab-5/exercise-3/) |
| [Lab 6](lab-6/exercise-1/) | Array-list growth and a block-based `GoodList`, with a timing driver |
| [Lab 7](lab-7/) | [Selection, insertion, and quick sort](lab-7/exercise-1/) with a [saved timing report](lab-7/exercise-1/report.txt); [search and sorted insertion](lab-7/exercise-2/) |
| [Lab 8, part 1](lab-8-part-1/exercise-1/) | Boolean-array membership container for a bounded integer range |
| [Lab 8, part 2](lab-8-part-2/exercise-1/) | Hash table using linked-list buckets |
| [Lab 9](lab-9/) | Binary search tree [parent links and paths to the root](lab-9/exercise-1/) and [node removal](lab-9/exercise-2/) |
| [Lecture 18](lecture-18/exercise-1/) | Binary search tree insertion, in-order traversal, and search |

Start with an exercise's `main.cpp` for its driver, then follow the local header includes. `test.cpp` records the supplied checks. Repeated header names belong to different exercises; build from the selected exercise directory rather than combining projects.

## Build and run

The source and Makefiles target a GNU/Linux-style environment. You need GCC's C++ compiler (`g++`) with C++11 or later support. Some exercises use GNU-specific headers such as `bits/stdc++.h` and `bits/types/time_t.h`; some tests use POSIX facilities such as `unistd.h` and `popen`.

For the introductory program, run these commands from the repository root in a POSIX shell:

```sh
cd lab-1/hello-ucm
g++ -std=c++11 -g -I. main.cpp -o app
./app
```

The source prints:

```text
Hello UC Merced
```

The direct compiler command follows the compile step in the local Makefile. For another exercise, change to its directory and compile its `main.cpp` the same way. Run programs that read local data from that directory: `WordleHelper` opens `answers.txt` and `allowed.txt` by relative name, and the scheduling driver can read the included `tasks.txt` through standard input. Lab 2's `main.cpp` is empty, so it does not provide an interactive Wordle application.

### Existing tests

Every `test.cpp` includes `igloo/igloo.h`. The Igloo test framework is an external prerequisite and is not bundled in this repository. With its headers on the compiler's include path, the direct test build is:

```sh
# Run inside the selected exercise directory.
g++ -std=c++11 -g -I. test.cpp -o coursework-tests
./coursework-tests --output=color
```

If Igloo is stored outside the compiler's default include directories, add `-I/path/to/igloo/include` pointing to the directory containing `igloo/`. The Lab 1 tests invoke `g++` themselves to compile and run `main.cpp`, so the compiler must also be on `PATH`.

## Archive notes

- The commands above were checked against the source and Makefiles, but compilation and test execution have not been verified for this documentation update. A compatible GCC/Igloo environment is required to establish current build and test results.
- The original Makefiles are retained. From Lab 5 onward, they write `~/workspace/.theia/launch.json`; the Lab 8, Lab 9, and Lecture 18 versions also remove and recreate `~/workspace/.theia/`. Review those recipes before running `make`. Direct compiler commands avoid these debugger configuration side effects.
- Existing `app` and `test` binaries are archived alongside the source. Rebuild for your environment rather than treating those binaries as portable or as evidence that the current source passes its tests.
- Some code retains starter comments and unfinished elements. For example, `WordleHelper::suggest()` returns a fixed list. The timing report in Lab 7 has no recorded hardware or compiler configuration, so its numbers should be read as historical results rather than reproducible benchmarks.
- Original source comments, tests, and attribution remain intact, including the Makefile credit to Angelo Kyrilov. No license file is present in this snapshot.
