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
    Create a graph, centred at 'centre' and randomly create generator points.
    PARAMETERS:
        centre: pair of coordinates in the form '(latitude, longitude)' in decimal.
        radius: radius of the final graph in metres.
        generatorCount: number of generators to be randomly generated.
    RETURNS:
        generators: list of generator points' node IDs.
        Gp: graph of network.
    RETURN TYPE:
        generators: list.
        Gp: networkx.MultiDiGraph object.

## manualSetup(centre, radius, generatorList):
    Create a graph, centred at 'centre' with generators at the specified points.
    PARAMETERS:
        centre: pair of coordinates in the form '(latitude, longitude)' in decimal.
        radius: radius of the final graph in metres.
        generatorList: list of generator coordinates in the form [ [lat, long], [lat, long], ... ]
    RETURNS:
        generators: list of generator points' node IDs.
        Gp: graph of network.
    RETURN TYPE:
        generators: list.
        Gp: networkx.MultiDiGraph object.

## euclid(generators, Gp):
    Assign every event point to a generator point based on Euclidean distance.
    PARAMETERS:
        generators: list of generator points' node IDs.
        Gp: graph of network.
    RETURNS:
        grList: list of assigned node IDs.
    RETURN TYPE:
        grList: list of lists, in the form [ [ID, ID, ... ], [ID, ID, ... ], ... ]

## taxicab(generators, Gp, griddir):
    Assign every event point to a generator point based on Manhattan distance.
    PARAMETERS:
        generators: list of generator points' node IDs.
        Gp: graph of network.
        griddir: list of coordinates of two adjacent, grid-aligned intersections
            in the form [ [lat, long], [lat, long] ]
    RETURNS:
        grList: list of assigned node IDs.
    RETURN TYPE:
        grList: list of lists, in the form [ [ID, ID, ... ], [ID, ID, ... ], ... ]

## network(generators, Gp):
    Assign every event point to a generator point based on network-based distance.
    PARAMETERS:
        generators: list of generator points' node IDs.
        Gp: graph of network.
    RETURNS:
        grList: list of assigned node IDs.
    RETURN TYPE:
        grList: list of lists, in the form [ [ID, ID, ... ], [ID, ID, ... ], ... ].

## comparison(test, base):
    Compares two grLists and gives match statistics.
    PARAMETERS:
        test: list of assigned node IDs.
        base: list of assigned node IDs.
    RETURNS:
        misclass: list of node IDs that were mismatches.
        acc: accuracy rate (100 = 100%)
    RETURN TYPE:
        misclass: list.
        acc: float.

## graphIt(Gp, nodesList, colours, title):
    Creates a graph of nodesList and saves to disk.
    PARAMETERS:
        Gp: graph of network area.
        nodesList: list of lists of node IDs, in the form [ [ID, ID, ... ], [ID, ID, ... ], ... ].
        colours: list of hex colours (must be as long as the number of lists in nodesList).
        title: file will be saved as 'title.png'
