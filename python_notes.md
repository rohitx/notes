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