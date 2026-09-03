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






