# Plotly Notes

I do not wish to copy the entire plotly manual that exits on the plotly website. But I hope this page will get me quickly what I usually do at work

## Automating a plotly routine

```{py}
def plot_plotly(dataframe):
    """
    Plots all of the columns in a given dataframe as a stacked plot.

    Note: Plotly is extremely slow when it comes to plotting data points
    greater than 100,000. So, this program will quit if the size is larger.

    Example:
    ---------
    df = pd.DataFrame()
    df['x'] = np.array([0, 1, 2])
    df['y1'] = np.array([10, 11, 12])
    df['y2'] = np.array([100, 110, 120])
    df['y3'] = np.array([1000, 1100, 1200])
    df['y4'] = np.array([2000, 3000, 1000])

    # Selecting first four columns
    df1 = df.iloc[:, :4]

    plot_plotly(df1)
    """

    if dataframe.shape[0] >= 100000:
        print "Data Frame too Large to plot"
    return None

    d = {}
    spec_list = []
    for i in np.arange(dataframe.shape[1] - 1):
        d["trace{0}".format(i)] = go.Scatter(x=list(dataframe.iloc[:, 0].values), y=list(dataframe.iloc[:, i + 1].values))
        spec_list.append([{}])

    fig = tools.make_subplots(rows=dataframe.shape[1] - 1, cols=1, specs=spec_list,
                              shared_xaxes=True, shared_yaxes=False,
                              vertical_spacing=0.1)

    for index, key in enumerate(d):
        fig.append_trace(d[key], index + 1, 1)
    return plot(fig)  
```
