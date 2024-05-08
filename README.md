# Installation Information
This program requires specific software to run.
Install Anaconda from the Windows installer at `anaconda.com/download`.
Navigate to the `\anaconda3` documentary and run the following command:
`conda_ create -n ox -c conda-forge --strict-channel-priority osmnx jupyterlab`.
Once this is complete, launch Anaconda Navigator and make sure you are running on `ox`, not `base`.
Run Jupyter Notebook and open the `voronoi.ipynb` file.
Run the first two cells (module imports and function definitions) - the program is then ready to use.

# Documentation

## autoSetup(centre, radius, generatorCount):
    Create a graph, centred at `centre` and randomly create generator points.
    PARAMETERS:
        centre: pair of coordinates in the form `(lat, long)` in decimal.
        radius: radius of the final graph in metres.
        generatorCount: number of generators to be randomly generated.
    RETURNS:
        generators: list of generator points' node IDs.
        Gp: graph of network.
    RETURN TYPE:
        generators: list.
        Gp: networkx.MultiDiGraph object.

## manualSetup(
