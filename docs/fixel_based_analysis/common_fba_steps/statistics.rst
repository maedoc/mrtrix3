Statistical analysis is performed using `connectivity-based fixel enhancement <http://www.ncbi.nlm.nih.gov/pubmed/26004503>`_, with a separate analysis for FD, FC, and FDC as follows::

     fixelcfestats fd files.txt design_matrix.txt contrast_matrix.txt input_tracks_2_million_sift.tck stats_fd
     fixelcfestats log_fc files.txt design_matrix.txt contrast_matrix.txt input_tracks_2_million_sift.tck stats_log_fc
     fixelcfestats fdc files.txt design_matrix.txt contrast_matrix.txt input_tracks_2_million_sift.tck stats_fdc

Where the input files.txt is a text file containing the filename of each file (i.e. not the full path) to be analysed inside the input fixel directory, each filename on a separate line. The line ordering should correspond to the lines in the design_matrix.txt. Note that for correlation analysis, a column of 1's will not be automatically included (as per FSL randomise). Note that fixelcfestats currently only accepts a single contrast. However if the opposite (negative) contrast is also required (i.e. a two-tailed test), then use the :code:`-neg` option. Several output files will generated all starting with the supplied prefix.

.. NOTE:: We recommend having no more than 500,000 fixels in the analysis_fixel_mask (you can check this by :code:`mrinfo -size ../template/fixel_template/mask.mif`, and looking at the size of the image along the 1st dimension), otherwise :ref:`fixelcfestats` will run out of RAM. A mask with 500,000 fixels will require a PC with 128GB of RAM for the statistical analysis step. To reduce RAM requirements, you could reduce the number of fixels by  reducing the extent of upsampling, or apply a higher threshold when computing the fixel analysis mask (at the risk of removing WM regions from your analysis).
