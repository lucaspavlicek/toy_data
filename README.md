# Generating dummy data to mimic a given dataset
This is specifically intended for Telescope Array data. There are two notebook files:

## toy_data.ipynb
### Organization
- The first code cell will generate toy data for a given input dataset, for each primary ID in ```mcip```, using libraries.
- The second code cell is my own code from pretty much scratch that makes toy data. This cell is for my own education.
- The third code cell has been used to check my work.

### General method used
1. Map each parameter in the data to a standard normal distribution by using a quantile transform.
2. Compute the covariance matrix of all of the normalized parameters.
3. Generate multivariate Gaussian samples with a mean of zero and covariance found previously.
4. Inverse quantile transform the generated samples to mimic the input data.

## compare_datasets.ipynb
This notebook creates a bunch of plots to check that the toy data and original data are similar. There is code for the following:
1. Creating a table of means along each parameter
   - This does not work when I try to save the figure, because plt.table works differently from other types of plots.
   - I don't think this is that important, so I am leaving it broken.
2. Plotting two correlation coefficient matrices as heatmaps.
3. Creating overlayed histograms for each parameter in the datasets.
4. Creating overlayed histograms of the full data projected onto a bunch of random lines.
   - I did this because it is possible for two distinct multivariate distributions to have the same marginal distributions, although I'm not sure this is something we even need to worry about in our case. I made this just in case.
   - By checking along random lines, we can help reassure ourselves.
