Connectomics programming tasks
Complete the tasks below using Python in one or multiple Jupyter notebooks. Ensure that the results of
your cells are displayed when saving and submitting the notebooks. When you install libraries, you can do
so in the notebook or outside of it.
Task 1. Loading and displaying electron microscopy (EM) data
The MICrONS dataset is one of the largest publicly available EM connectomics datasets with a volume of
~1mm3
. To display and store this data efficiently, these datasets are chunked into blocks of data and
downsampled multiple times to enable viewing of the data at different zoom levels. Each downsampled
layer (also called a “mip”) is stored independently. The Python library cloudvolume is the de facto
standard for interacting with these datasets. It handles all the details of the chunking and downsampling,
and allows interactions with these datasets similar to how you would index into a numpy array.
Use cloudvolume to gather a slice through the EM dataset and display it as an image. Choose a
resolution that is manageable while still providing a clear image of the data. The view should be similar to
how you see the data here. The slice should cover the entire dataset in x and y, and 1 pixel in the z
dimension. Follow cloudvolume’s documentation for installing it, instantiating a cloudvolume object for the
dataset, and extracting the slice.
A few helpful notes: The dataset uses the precomputed format, and the path to it is below. You will not
need any credentials. Use “use
_
https=True” when instantiating the cloudvolume object for the dataset,
which tells cloudvolume not to look for credentials and to be in read-only mode. If your bounding box
exceeds the dataset bounds, you may need to use “fill
_
missing=True”
.
Path to MICrONS EM data:
precomputed://https://bossdb-open-data.s3.amazonaws.com/iarpa
microns/minnie/minnie65/em



Task 2. Connectivity vs distance
Connections between neurons are mediated by synapses. For each synapse, there is a presynaptic
neuron and a postsynaptic neuron. It has been postulated multiple times that the likelihood for two
neurons to be synaptically connected this way is inversely related to their distance (here: distance
between cell bodies). Here, we will analyze that in the MICrONS dataset using the outgoing synapses
(those on the axon) of a handful of cells. For that, you have access to two pandas dataframes:
1. A connections dataframe containing the outgoing connections for 66 neurons. Their connections
are with all kinds of neurons in the dataset.
2. A locations dataframe containing the cell body locations of all neurons in the dataset, along with
their corresponding cell types.
Both dataframes can be loaded via “pd.read_feater(<path to dataframe>)”. The locations dataframe
allows you to calculate distances between cells, and the connections dataframe contains the information
about which cells are connected. You can assume that cell pairs not listed in the connections dataframe
are not connected.
Perform an analysis that quantifies the connection probability dependent on cell-cell distance. We refer to
connection probability as the fraction of connected cell pairs over the total number of potentially connected cell pairs for a given distance. Your analysis should produce one or multiple plots. Using a text
or markdown box, describe your findings briefly.
DataFrames
connections dataframe:
https://github.com/sdorkenw/ConnectomicsProgrammingTask/blob/main/data/task_connections_1507.feat
her
Columns:
- pre_pt_root_id: Presynaptic neuron ID
- post_pt_root_id: Postsynaptic neuron ID
- syn_count: Number of synapses between the same pre- and postsynaptic neurons
cell body dataframe:
https://github.com/sdorkenw/ConnectomicsProgrammingTask/blob/main/data/task_cell_body_locations_1
507.feather
Columns:
- pt_root_id: neuron ID
- pt_position_{x, y, z}: Coordinate in nanometers
- coarse_cell_type: coarse cell type label (excitatory, inhibitory)
- cell_type: fine cell type label






