# LoLalytics Tierlist ~An~alyzer

This Python code allows you to ~an~alyze the champion tierlist for the popular MOBA game League of Legends. Using data from the website lolalytics.com, this code retrieves champion tier information for multiple patches, aggregates the data, and then visualizes the information using Plotly.

## Installation
Install the required packages using pip:

```pip install -r requirements.txt```

You will also need to have the Chrome WebDriver executable installed on your system. You can download it from the following [link](https://sites.google.com/chromium.org/driver/?pli=1)

## Functions
The main functions in the code are:

### get_champion_tierlist(patch:str = '13.9'):
Retrieves the champion tierlist information for a specific patch.

Input: patch is a string indicating the patch version in the format 'X.Y', where X and Y are integers representing the major and minor patch versions respectively.
<br>Output: A dictionary containing the tierlist information for each champion.

### get_tierlist(patch_list: list):
Retrieves the champion tierlist information for a list of patches, aggregates the data and returns a Pandas DataFrame.

Input: patch_list is a list of strings indicating the patch versions to retrieve the information for.
<br>Output: A Pandas DataFrame containing the aggregated tierlist information for each champion and patch combination.

### fig_tierlist(tierlist_df: pd.DataFrame, information: str = "winRate"):
Creates a line plot using Plotly to visualize how the chosen tierlist information (winrate, pickrate, banrate, etc.) varies between different champions and patches.

Input: tierlist_df is a Pandas DataFrame containing the tierlist information for each champion and patch combination. information is a string indicating the tierlist information to use for the plot.
<br>Output: A Plotly line plot showing the chosen tierlist information for each champion and patch combination.

### fig_tierlist_grouped(tierlist_df: pd.DataFrame, information: str = "winRate", method: str = "mean"):
Creates a line plot using Plotly to visualize how the chosen tierlist information (winrate, pickrate, banrate, etc.) varies for each champion, grouped by the chosen method (mean, median, std, max, or min).

Input: tierlist_df is a Pandas DataFrame containing the tierlist information for each champion and patch combination. information is a string indicating the tierlist information to use for the plot. method is a string indicating the grouping method to use for the plot.
<br>Output: A Plotly line plot showing the chosen tierlist information for each champion, grouped by the chosen method.

## Usage
The fig_tierlist and fig_tierlist_grouped functions are used to visualize changes in champion performance across different patches in the game League of Legends. The get_tierlist function is used to collect data from lolalytics.com for the specified patch list, which is used as input for these two functions.

* ### fig_tierlist
The fig_tierlist function takes a pandas DataFrame containing champion tierlist data and an information parameter specifying the type of information to display, such as "winRate". It then creates a line plot that displays the specified information for each champion across all patches in the DataFrame.

```
# Load data using get_tierlist function
patch_list = [13.9, 13.8, 13.7]
tier_data = get_tierlist(patch_list)

# Generate figure
fig = fig_tierlist(tier_data, information="winRate")
fig.show()
```

* ### fig_tierlist_grouped
The fig_tierlist_grouped function is similar to fig_tierlist, but it groups champion tierlist data by a specified method, such as mean or median. This function takes the same inputs as fig_tierlist, but also includes an additional method parameter that specifies how the data should be grouped.

```
# Load data using get_tierlist function
patch_list = [13.9, 13.8, 13.7]
tier_data = get_tierlist(patch_list)

# Generate figure
fig = fig_tierlist_grouped(tier_data, information="winRate", method="mean")
fig.show()
```

The method parameter can take the values "mean", "median", "std", "max", or "min". These correspond to the mean, median, standard deviation, maximum, and minimum values of the specified information for each champion across all patches. The resulting figure displays the information for each champion grouped by the specified method.
