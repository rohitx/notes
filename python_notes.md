# Python Notes

These notes are collections of questions I have asked and answers I have found on Stackoverflow. I decided to put them together into one place for the ease of finding them when needed. Where necessary I have included the stackoverflow link. I have also tried to include codes and tricks that I found online or in books. 

The notes are divided into two groups: pandas and python. 


## pandas

### Convert range to timestamp in Pandas

Suppose I have the following: 

```{py}
In [12]: test.head()
Out[12]:
   TIME  DATA
0     0   729
1    10   568
2    20   412
3    30   988
4    40   494
```

I would like to convert 'TIME' into datetime. Do the following:

```{py}
In [13]: test['TIME'] = pd.to_datetime('2016-09-20') + pd.to_timedelta(time, 'ms')

In [14]: test.head()
Out[14]:
                     TIME  DATA
0 2016-09-20 00:00:00.000   729
1 2016-09-20 00:00:00.010   568
2 2016-09-20 00:00:00.020   412
3 2016-09-20 00:00:00.030   988
4 2016-09-20 00:00:00.040   494
```

Here `we assumed that the starting date was 09/20/2016`. I asked this question on [stackoverflow](http://stackoverflow.com/questions/39713381/convert-range-to-timestamp-in-pandas) 

## python

### Convert human readable time to unix timestamp

```{py}
import datetime
def input_time(start_time, stop_time):
    """Converts human readable time into unix timestamp
    Example
    --------
        >>> start = '2016-11-23 00:00:00'
        >>> stop = '2016-11-24 00:00:00'

        >>> start_time, stop_time = input_time(start, stop)
    """
    t1 = datetime.datetime.strptime(start_time, "%Y-%m-%d %H:%M:%S")
    t2 = datetime.datetime.strptime(stop_time, "%Y-%m-%d %H:%M:%S")
    start = (t1 - datetime.datetime(1970, 1, 1)).total_seconds()
    end = (t2 - datetime.datetime(1970, 1, 1)).total_seconds()

    return int(start * 1000), int(end * 1000)
```

### Convert unix timestamp to human readable time

```{py}
import datetime
d1 = datetime.datetime.utcfromtimestamp(round(int(t1 / 1000.))).strftime('%Y-%m-%d %H:%M:%S')
```
where t1 is the time in unix. 