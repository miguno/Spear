# SPEAR

The reference implementation of the SPEAR ranking algorithm in Python.

## Features

The purpose of this reference implementation is to make the behavior of the
SPEAR algorithm easy to understand. It uses straight-forward, non-optimized code
so that the reader is not confused by highly optimized code.

The SPEAR algorithm takes a _list of user activities on resources_ as input, and
returns _a ranked list of users by expertise scores_ and _a ranked list of
resources by quality scores_, respectively.

## Using SPEAR to simulate the HITS algorithm

You can also use this library to simulate the [HITS
algorithm](https://en.wikipedia.org/wiki/HITS_algorithm) of Jon Kleinberg by
supplying a credit score function `C(x) = 1` to the SPEAR algorithm.

See the documentation of `Spear.run()`.

## Installing SPEAR

1.  Install [SciPy/NumPy](http://www.scipy.org/), which is required by SPEAR.
2.  Install SPEAR:

    ```shell
    $ pip install Spear
    ```

    After installation, `import spear` in your Python scripts.

An alternative installation method is downloading the code directly from this
git repository.

## Updating SPEAR

Update SPEAR with:

```shell
$ pip install --upgrade Spear
```

## Usage

The algorithm requires a list of user activities on resources as input. More
specifically, it requires a list of `(timestamp, user, resource)` tuples.

```python
>>> import spear
>>> activities = [
... (datetime.datetime(2010,7,1,9,0,0), "alice", "http://www.quuxlabs.com/"),
... (datetime.datetime(2010,8,1,12,45,0), "bob", "http://www.quuxlabs.com/"),
... ]
>>> spear_algorithm = spear.Spear(activities)
>>> expertise_results, quality_results = spear_algorithm.run()
```

Get the top user and their _expertise score_:

```python
>>> expertise_score, user = expertise_results[0]
>>> print "%s => %.4f" % (user, expertise_score)
alice => 0.5858
```

Get the top resource and its _quality score_:

```python
>>> quality_score, resource = quality_results[0]
>>> print "%s => %.4f" % (resource, quality_score)
http://www.quuxlabs.com/ => 1.0000
```

## More information

You can find more information about the SPEAR algorithm at:

- [Telling Experts from Spammers: Expertise Ranking in Folksonomies](http://portal.acm.org/citation.cfm?id=1571941.1572046)
  by Michael G. Noll, Ching-man Au Yeung, et al.,
  SIGIR 09: Proceedings of 32nd International ACM SIGIR Conference
  on Research and Development in Information Retrieval, Boston, USA,
  July 2009, pp. 612-619, ISBN 978-1-60558-483-6

## License

The code is licensed to you under version 2 of the GNU General Public License.

## Copyright

Copyright 2009-2010 Michael G. Noll <http://www.michael-noll.com/>,
Ching-man Au Yeung <https://ayeung.dev/>
