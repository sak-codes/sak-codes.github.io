# Google Summer of Code 2023

## Extending the data structures and algorithms along with providing C++ backend

**Project Mentors**: Gagandeep Singh, Ivan Ogasawara, Smit Lunagariya, Ever Vino, Alexandre de Siqueira, Agustina Pesce, Saransh Chopra

This is the final report of the entire GSoC 2023  for the project titled as **Extending the data structures and algorithms along with providing C++ backend**. The complete description of the project implementation and discussions of the entire program is available at my [personal blog site](https://sak-codes.github.io).

### About Me

I am **Sakshi Oza**, final year Masters student at Indian Institute of Technology, Gandhinagar.

### Project Overview: Phase-wise short description

I divided the whole project into three main phases to work on the specific topics that were supposed to be implemented during the GSoC.

1. **Community Bonding & Pre-GSOC**: During this phase, I mainly focused
on the easier topics that help me to get started with the official coding
timeline. I dedicated my efforts to gaining a thorough understanding of the codebase.

2. **Phase 1**: This phase consists of the official coding before prior to
the mid evaluation. This phase was mainly focused on extending the existing
scope of data structures and algorithms as well as fixing the existing
issues.

2. **Phase 2**: This phase consists of the official coding after the
the mid evaluation. This phase included working on some new data structures
along with adding the CPP backend to the current algorithms under the
`linear_data_structures` submodule.


### Pull Requests
This section describes the actual work done during the coding period in terms of merged pull requests.


**Community Bonding & Pre-GSOC**

- [#516](https://github.com/codezonediitj/pydatastructs/pull/516) - This PR
implements a method in `DSU` to find the size of the group of the given key.

- [#517](https://github.com/codezonediitj/pydatastructs/pull/517) - This PR
adds a method in the class `Trie` to check if the string as inserted before.

- [#521](https://github.com/codezonediitj/pydatastructs/pull/521) - This PR
implements a method to print all the members of the same group in `DSU`.

**Phase 1**

- [#530](https://github.com/codezonediitj/pydatastructs/pull/530) - This PR
closes the [issue-478](https://github.com/codezonediitj/pydatastructs/issues/478) by implementing the network flow algorithms: Edmond Karp.

- [#534](https://github.com/codezonediitj/pydatastructs/pull/534) - This PR was built on the top of the above PR to add the Dinic algorithm for network flow.

- [#535](https://github.com/codezonediitj/pydatastructs/pull/535) - This PR
closes the [issue-436](https://github.com/codezonediitj/pydatastructs/issues/436) by implementing a `test` function that helps in testing
the library installation as well as supports submodule specific tests.

- [#537](https://github.com/codezonediitj/pydatastructs/pull/537) - This PR
implements lower bound and upper bound in the BST data structure similar to
CPP's STL.

**Phase 2**

- [#538](https://github.com/codezonediitj/pydatastructs/pull/538) - This PR closes an [issue-390](https://github.com/codezonediitj/pydatastructs/issues/390) on adding a `Multiset` data structure similar to CPP's STL.

- [#539](https://github.com/codezonediitj/pydatastructs/pull/539) - This PR
adds Lazy Segment Tree implementation.

- [#540](https://github.com/codezonediitj/pydatastructs/pull/540) - This PR
focuses on the CPP backend of the project targeting the sorting algorithm by starting with `bubble_sort`.

- [#542](https://github.com/codezonediitj/pydatastructs/pull/542) - This PR
completed CPP backend of `selection_sort`.

- [#543](https://github.com/codezonediitj/pydatastructs/pull/543) - This PR
completed CPP backend of `insertion_sort` and `is_ordered`.

- [#544](https://github.com/codezonediitj/pydatastructs/pull/544) - This PR
extends CPP backend for search algorithms: `linear_search`, `binary_search`, and `jump_search`.

### Examples

1. Using the `test` function

```python
>>> from pydatastructs import test
>>> test(["graphs"])
============================= test session starts ==============================
platform darwin -- Python 3.8.16, pytest-7.3.1, pluggy-1.0.0
rootdir: /Users/thebigbool/repos/pydatastructs
plugins: cov-4.1.0, xdist-3.3.1, anyio-3.7.0
collected 11 items

pydatastructs/graphs/tests/test_adjacency_list.py .                      [  9%]
pydatastructs/graphs/tests/test_adjacency_matrix.py .                    [ 18%]
pydatastructs/graphs/tests/test_algorithms.py .........                  [100%]

============================== 11 passed in 0.05s ==============================
```

We can also test an imported submodule in the similar way:

```python
>>> from pydatastructs import graphs
>>> test([graphs])
============================= test session starts ==============================
platform darwin -- Python 3.8.16, pytest-7.3.1, pluggy-1.0.0
rootdir: /Users/thebigbool/repos/pydatastructs
plugins: cov-4.1.0, xdist-3.3.1, anyio-3.7.0
collected 11 items

pydatastructs/graphs/tests/test_adjacency_list.py .                      [  9%]
pydatastructs/graphs/tests/test_adjacency_matrix.py .                    [ 18%]
pydatastructs/graphs/tests/test_algorithms.py .........                  [100%]

============================== 11 passed in 0.02s ==============================
```

2. Using a `Multiset`

```python
>>> from pydatastructs.miscellaneous_data_structures import Multiset
>>> ms = Multiset()
>>> ms.add(5)
>>> ms.add(5)
>>> ms.add(3)
>>> ms.add(7)
>>> len(ms)
4
>>> 5 in ms
True
>>> 2 in ms
False
```

3. Using a CPP backend

```python
>>> from pydatastructs import OneDimensionalArray, Backend, linear_search
>>> array = OneDimensionalArray(int, [1, 2, 5, 7, 10, 29, 40])
>>> linear_search(array, 5, backend=Backend.CPP)
2
>>> linear_search(array, -5, backend=Backend.CPP) # not found
>>>
```

### Conclusion

This summer has been a great learning experience. I am grateful to my
mentors, [Gagandeep Singh](https://github.com/czgdp1807), and [Smit Lunagariya](https://github.com/Smit-create) for always helping me with
the new concepts, reviewing my PRs and providing quick responses.