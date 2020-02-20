This document describe ways to workaround GitHub API, especially the rate limit.

# Workaround for downloading files

## How to do it via GitHub API
Let's say you would like to extract files from this [commit](https://github.com/INRIA/spoon/commit/4ee28da1dcdb39d34edc32cd8bbc2b1d2bf0183b). The organization name is `INRIA`, the project name is `spoon` and the commit SHA is `4ee28da1dcdb39d34edc32cd8bbc2b1d2bf0183b`. In this commit, three files were changed:
1. `src/main/java/spoon/reflect/factory/TypeFactory.java`
2. `src/test/java/spoon/test/prettyprinter/SniperDoubleBoundTest.java`
3. `src/test/java/spoon/test/prettyprinter/testclasses/DoubleBound.java`

To get `src/main/java/spoon/reflect/factory/TypeFactory.java` from `INRIA/spoon` with commit SHA ID `4ee28da1dcdb39d34edc32cd8bbc2b1d2bf0183b`, we can use the following GitHub API call:
```bash
curl https://raw.githubusercontent.com/INRIA/spoon/4ee28da1dcdb39d34edc32cd8bbc2b1d2bf0183b/src/main/java/spoon/reflect/factory/TypeFactory.java
```

But currently, the GitHub API rate limit is 5000 requests per hour with OAuth.

## How to do it via GitHub mirror
I will use [jsDelivr](https://www.jsdelivr.com) as an example of GitHub mirror.

To get `src/main/java/spoon/reflect/factory/TypeFactory.java` from `INRIA/spoon` with commit SHA ID `4ee28da1dcdb39d34edc32cd8bbc2b1d2bf0183b`, we can use the following jsDelivr API call:
```bash
curl https://cdn.jsdelivr.net/gh/INRIA/spoon@4ee28da1dcdb39d34edc32cd8bbc2b1d2bf0183b/src/main/java/spoon/reflect/factory/TypeFactory.java
```

This can be easily parallelized and exceed 5000 requests per hour.
