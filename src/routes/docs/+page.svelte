<script lang="ts">
  const categories = [
    {
      title: 'Getting Started',
      sections: [
        {
          id: 'introduction',
          title: 'Introduction',
          content: `
            <p>SciPathJ (Segmentation and Classification of Images - Pipeline for the Analysis of Tissue Histopathology) is a Java-based software designed for automated analysis of H&E-stained microscopy images.</p>
            <p>The software provides a complete pipeline for:</p>
            <ul>
              <li>Automated segmentation of cells, nuclei, cytoplasm, and vessels</li>
              <li>Extraction of 150+ morphological and color features</li>
              <li>Custom cell class definition and training</li>
              <li>Machine learning-based cell classification using XGBoost</li>
              <li>Batch processing of entire image folders</li>
            </ul>
          `
        },
        {
          id: 'installation',
          title: 'Installation',
          content: `
            <h3>System Requirements</h3>
            <ul>
              <li><strong>RAM:</strong> 4 GB minimum (8 GB recommended for large images)</li>
              <li><strong>Disk Space:</strong> 500 MB for the installer + 700 MB for the installed program</li>
              <li><strong>Operating System:</strong> Windows 10/11 (64-bit)</li>
            </ul>
            
            <h3>Standalone Installation</h3>
            <p>SciPathJ is distributed as a Windows executable installer that guides you through the installation process:</p>
            <ol>
              <li>Download the installer (.exe) from the <a href="https://drive.google.com/file/d/1v-_iiADQWxqjXDaBkCGaNjiFPi2Ngynn/view?usp=drive_link" target="_blank" rel="noopener noreferrer">Download page</a></li>
              <li>Double-click the installer to launch the setup wizard</li>
              <li>Follow the on-screen instructions to complete the installation</li>
              <li>Launch SciPathJ from the Start Menu or desktop shortcut</li>
            </ol>
            <p>The installer will automatically handle all dependencies and create the necessary shortcuts for easy access.</p>
            
            <h3>ImageJ/Fiji Plugin (Legacy Version)</h3>
            <div class="warning-box">
              <p><strong>Note:</strong> The ImageJ/Fiji plugin version is a discontinued legacy version and is no longer actively maintained. It may not include the latest features and improvements available in the standalone version.</p>
            </div>
            <p>For instructions on how to install the legacy plugin version, please watch our video tutorial:</p>
            <p><a href="/tutorials#plugin-installation" class="btn btn-secondary">Watch Plugin Installation Tutorial</a></p>
          `
        },
        {
          id: 'gui',
          title: 'Main Interface',
          content: `
            <h3>Overview</h3>
            <p>The SciPathJ main interface is designed to be intuitive and user-friendly, providing easy access to all analysis tools and settings.</p>
            
            <div class="gui-image-container">
              <!-- Replace YOUR_GOOGLE_DRIVE_ID with the actual file ID from Google Drive -->
              <img src="https://lh3.googleusercontent.com/d/1y0WfhMlXYUYki-wQbup-D03Hw2dlsMVa" alt="SciPathJ GUI Overview" class="docs-image" />
              <p class="image-caption">SciPathJ Main Interface Overview</p>
            </div>
    
            <h4>1. Workflow Pipeline</h4>
            <p>The top bar displays the sequential steps of the analysis pipeline. You can click on each step to configure its specific parameters:</p>
            <ul>
              <li><strong>Vessel Segmentation:</strong> Detect and delineate vascular structures.</li>
              <li><strong>Nuclear Segmentation:</strong> Identify cell nuclei using hematoxylin staining.</li>
              <li><strong>Cell Creation:</strong> Combine nuclei and cytoplasm to define complete cells.</li>
              <li><strong>Feature Extraction:</strong> Calculate morphological and intensity measurements.</li>
              <li><strong>Cell Classification:</strong> Train and apply machine learning models to classify cells.</li>
              <li><strong>Final Analysis:</strong> Generate summary statistics and reports.</li>
            </ul>
    
            <h4>2. Global Settings & Navigation</h4>
            <p>Located at the top right:</p>
            <ul>
              <li><strong>Display Settings:</strong> Control overlay colors, transparency, and visualization modes.</li>
              <li><strong>Main Settings:</strong> Configure general preferences, memory allocation, and output options.</li>
              <li><strong>Change Folder:</strong> Select a different directory for analysis.</li>
            </ul>
    
            <h4>3. Image Selection & Canvas</h4>
            <ul>
              <li><strong>Left Sidebar:</strong> Displays thumbnails of images in the current folder for quick switching.</li>
              <li><strong>Central Canvas:</strong> Shows the active image with segmentation overlays. Use the mouse wheel to zoom and click-drag to pan.</li>
              <li><strong>Zoom Controls:</strong> Located at the top right of the canvas for precise magnification adjustment.</li>
            </ul>
    
            <h4>4. ROI Management & Tools</h4>
            <p>The bottom toolbar provides tools for managing Regions of Interest (ROIs):</p>
            <ul>
              <li><strong>Save ROIs:</strong> Export detected regions as images or data files.</li>
              <li><strong>Clear All:</strong> Remove all current segmentations from the image.</li>
              <li><strong>ROI Toggles:</strong> Show/hide specific types of detections (Vessels, Nuclei, Cytoplasms, Cells).</li>
              <li><strong>Analysis Tools:</strong> Access Stats, Averages, and Cluster Colors for the current image.</li>
            </ul>
    
            <h4>5. Execution Controls</h4>
            <p>The bottom bar manages the analysis process:</p>
            <ul>
              <li><strong>Status Message:</strong> Displays the result of the last operation.</li>
              <li><strong>Progress Bar:</strong> Shows real-time progress of the current analysis step.</li>
              <li><strong>Start/Stop Analysis:</strong> Control the execution of the pipeline.</li>
              <li><strong>Back:</strong> Return to the previous screen or folder selection.</li>
            </ul>
          `
        }
      ]
    },
    {
      title: 'Configuration',
      sections: [
        {
          id: 'main-settings',
          title: 'Main Settings',
          content: `
            <h3>Overview</h3>
            <p>The Main Application Settings panel allows you to configure global parameters for image analysis and data export.</p>
            
            <div class="gui-image-container">
              <img src="https://lh3.googleusercontent.com/d/1v4uFGjdB4LNyuUqeuZCEXsKcPmsJwjJA" alt="Main Settings Panel" class="docs-image" />
              <p class="image-caption">Main Application Settings</p>
            </div>
    
            <h4>Scale & Units</h4>
            <ul>
              <li><strong>Pixels per Micrometer:</strong> Define the resolution of your images. This value is crucial for accurate area and length measurements.</li>
              <li><strong>Scale Unit:</strong> The unit of measurement (e.g., µm).</li>
              <li><strong>Scale Preview:</strong> Shows a real-time conversion example based on your settings.</li>
            </ul>
            
            <h4>Other Settings</h4>
            <ul>
              <li><strong>CSV Export:</strong> Configure options for exporting analysis results to CSV files.</li>
              <li><strong>Ignore Distance:</strong> Set parameters for excluding regions based on distance.</li>
            </ul>
          `
        },
        {
          id: 'display-settings',
          title: 'Display Settings',
          content: `
            <h3>Overview</h3>
            <p>The Display Settings panel allows you to customize how Regions of Interest (ROIs) are visualized on the image canvas. You can configure settings independently for Vessel, Nucleus, Cytoplasm, Cell, and Ignore ROIs.</p>
            
            <div class="gui-image-container">
              <img src="https://lh3.googleusercontent.com/d/1WsUJPLFmQARwEjDHR6sHx9qOwFWbU8D7" alt="Display Settings Panel" class="docs-image" />
              <p class="image-caption">Display Settings</p>
            </div>
    
            <h4>ROI Display Options</h4>
            <ul>
              <li><strong>Border Color:</strong> Choose the color for the ROI boundaries.</li>
              <li><strong>Fill Opacity:</strong> Adjust the transparency of the ROI fill color (0-100%).</li>
              <li><strong>Border Width:</strong> Set the thickness of the ROI outlines.</li>
            </ul>
          `
        }
      ]
    },
    {
      title: 'Analysis Pipeline',
      sections: [
        {
          id: 'vessel-segmentation',
          title: 'Vessel Segmentation',
          content: `
            <h3>Overview</h3>
            <p>The Vessel Segmentation Settings panel controls the parameters for detecting vascular structures.</p>
            
            <div class="gui-image-container">
              <img src="https://lh3.googleusercontent.com/d/1_Gvig6gdgPI9UzAILkomI8RlKAAReTAR" alt="Vessel Segmentation Settings" class="docs-image" />
              <p class="image-caption">Vessel Segmentation Settings</p>
            </div>
    
            <h4>Thresholding</h4>
            <ul>
              <li><strong>Threshold Value:</strong> Set the intensity threshold (0-255) for identifying vessel candidates.</li>
            </ul>
            
            <h4>Size Filtering</h4>
            <ul>
              <li><strong>Min ROI Size (µm²):</strong> Minimum area required for a detected region to be considered a vessel.</li>
              <li><strong>Max ROI Size (µm²):</strong> Maximum allowed area for a vessel.</li>
            </ul>
            
            <h4>Processing</h4>
            <ul>
              <li><strong>Gaussian Blur Sigma:</strong> Controls the amount of smoothing applied before segmentation to reduce noise.</li>
              <li><strong>Apply Morphological Closing:</strong> Enable to close small gaps and smooth boundaries of detected vessels.</li>
            </ul>
          `
        },
        {
          id: 'nuclear-segmentation',
          title: 'Nuclear Segmentation',
          content: `
            <h3>Overview</h3>
            <p>The Nuclear Segmentation Settings panel uses the StarDist deep learning model for accurate nucleus detection.</p>
            
            <div class="gui-image-container">
              <img src="https://lh3.googleusercontent.com/d/1uo2SB1S37L0XicM5IgBZPFRsMUiyEzCv" alt="Nuclear Segmentation Settings" class="docs-image" />
              <p class="image-caption">Nuclear Segmentation Settings</p>
            </div>
    
            <h4>Model & Normalization</h4>
            <ul>
              <li><strong>StarDist Model:</strong> Select the pre-trained model (e.g., Versatile H&E nuclei).</li>
              <li><strong>Normalize Input:</strong> Enable input image normalization.</li>
              <li><strong>Percentiles:</strong> Adjust the bottom and top percentiles for intensity normalization.</li>
            </ul>
            
            <h4>Detection Thresholds</h4>
            <ul>
              <li><strong>Probability Threshold:</strong> Minimum probability score for a detected object to be accepted as a nucleus.</li>
              <li><strong>Overlap Threshold:</strong> Maximum allowed overlap between detected nuclei.</li>
            </ul>
            
            <h4>Processing Settings</h4>
            <ul>
              <li><strong>Number of Tiles:</strong> Split the image into tiles for processing (useful for large images).</li>
              <li><strong>Exclude Boundary:</strong> Exclude nuclei detected near the image edges.</li>
            </ul>
            
            <h4>Size Filtering</h4>
            <ul>
              <li><strong>Min Nucleus Size (µm):</strong> Minimum diameter/size for a nucleus.</li>
              <li><strong>Max Nucleus Size (µm):</strong> Maximum diameter/size for a nucleus.</li>
            </ul>
          `
        },
        {
          id: 'cell-creation',
          title: 'Cell Creation',
          content: `
            <h3>Overview</h3>
            <p>The Cytoplasm Segmentation Settings panel defines how cell boundaries are estimated around detected nuclei.</p>
            
            <div class="gui-image-container">
              <img src="https://lh3.googleusercontent.com/d/1yvshHSpyQA-wAPUhUaVKYEm8IX6xeh7h" alt="Cytoplasm Segmentation Settings" class="docs-image" />
              <p class="image-caption">Cytoplasm Segmentation Settings</p>
            </div>
    
            <h4>Voronoi Tessellation</h4>
            <ul>
              <li><strong>Voronoi Expansion:</strong> Controls the maximum expansion distance from the nucleus to define the cytoplasm.</li>
            </ul>
            
            <h4>Polynucleated Cells</h4>
            <ul>
              <li><strong>Merge Close Nuclei:</strong> Enable merging of nuclei that are close together to form polynucleated cells.</li>
              <li><strong>Merge Threshold (µm):</strong> Maximum distance between nuclei to be merged.</li>
              <li><strong>Max Nuclei Per Cell:</strong> Maximum number of nuclei allowed in a single cell.</li>
            </ul>
            
            <h4>Advanced Merging Filters</h4>
            <ul>
              <li><strong>Nucleus Area Limits:</strong> Min/Max area constraints for nuclei involved in merging.</li>
              <li><strong>Shape Constraints:</strong> Filter based on Circularity and Aspect Ratio.</li>
            </ul>
            
            <h4>Vessel Exclusion</h4>
            <ul>
              <li><strong>Exclude Vessel Areas:</strong> Prevent cell creation within detected vessel regions.</li>
            </ul>
            
            <h4>Size Filtering & Processing</h4>
            <ul>
              <li><strong>Cell Size Limits:</strong> Min/Max area constraints for the final cell.</li>
              <li><strong>Cytoplasm Area Limits:</strong> Min/Max area constraints for the cytoplasm region.</li>
              <li><strong>Gaussian Blur Sigma:</strong> Smoothing factor for image processing.</li>
              <li><strong>Morph Closing Radius:</strong> Radius for morphological closing operations.</li>
              <li><strong>Watershed Tolerance:</strong> Tolerance parameter for the watershed algorithm used in separation.</li>
            </ul>
          `
        },
        {
          id: 'feature-extraction',
          title: 'Feature Extraction',
          content: `
            <h3>Overview</h3>
            <p>The Feature Extraction Settings panel allows you to select which features to calculate for Cell, Nucleus, Cytoplasm, and Vessel ROIs.</p>
            
            <div class="gui-image-container">
              <img src="https://lh3.googleusercontent.com/d/1X86OPcZqakId3WwnNJpYwxmYAHVUt1NT" alt="Feature Extraction Settings" class="docs-image" />
              <p class="image-caption">Feature Extraction Settings</p>
            </div>
    
            <h4>Cell Features</h4>
            <p>Features are categorized into groups:</p>
            <ul>
              <li><strong>H&E Stain-Specific Features:</strong> Measurements related to Hematoxylin and Eosin staining (e.g., Mean, Stddev, Skew, Max for both stains).</li>
              <li><strong>Intensity Features:</strong> General intensity statistics (Mean, Min, Max, Median, Skew, Kurtosis, etc.).</li>
              <li><strong>Spatial Features:</strong> Measurements related to spatial distribution (e.g., Vessel Distance, Neighbor Count).</li>
            </ul>
            <p>You can use the "Select All" checkbox to quickly enable or disable all features in a category.</p>
          `
        },
        {
          id: 'cell-classification',
          title: 'Cell Classification',
          content: `
            <h3>Overview</h3>
            <p>The Unsupervised Classification Settings panel allows you to group cells based on their features without prior training.</p>
            
            <div class="gui-image-container">
              <img src="https://lh3.googleusercontent.com/d/1ur7IaUzLuWTH1gbfDwb2PQhyFte_OKPX" alt="Unsupervised Classification Settings" class="docs-image" />
              <p class="image-caption">Unsupervised Classification Settings</p>
            </div>
    
            <h4>Clustering Configuration</h4>
            <ul>
              <li><strong>Enable Unsupervised Classification:</strong> Toggle the classification process.</li>
              <li><strong>Clustering Algorithm:</strong> Select the algorithm to use (e.g., K-Means).</li>
              <li><strong>Number of Clusters (K):</strong> Define the number of groups to find.</li>
              <li><strong>Max Iterations:</strong> Set the maximum number of iterations for the algorithm to converge.</li>
            </ul>
            
            <h4>Feature Selection</h4>
            <p>Select the specific features to use for clustering (e.g., Cell Area, Cell Circularity, Eosin Mean). Only selected features will be used to determine the clusters.</p>
          `
        },
        {
          id: 'batch-analysis',
          title: 'Batch Analysis',
          content: `
            <h3>Overview</h3>
            <p>Batch analysis allows you to process multiple images automatically using the same settings.</p>
            
            <h4>Setting Up Batch Processing</h4>
            <p>Instead of selecting a single image, select a folder containing your images:</p>
            <ol>
              <li>Go to <strong>File > Open Folder</strong> or click the folder icon in the toolbar</li>
              <li>Select the folder containing your images</li>
              <li>Configure all settings panels with your desired parameters</li>
              <li>Click <strong>Process > Batch Analysis</strong> to start</li>
            </ol>
            
            <h4>Supported Formats</h4>
            <ul>
              <li>TIFF (.tif, .tiff)</li>
              <li>PNG (.png)</li>
              <li>JPEG (.jpg, .jpeg)</li>
              <li>NDPI (Hamamatsu scanner format)</li>
              <li>SVS (Aperio scanner format)</li>
            </ul>
            
            <h4>Output Organization</h4>
            <p>Batch processing creates an organized output structure:</p>
            <ul>
              <li>One subfolder per image with all results</li>
              <li>Combined CSV files with all features</li>
              <li>Summary statistics across all images</li>
            </ul>
            
            <h4>Progress Monitoring</h4>
            <p>The batch processing window shows:</p>
            <ul>
              <li>Current image being processed</li>
              <li>Overall progress percentage</li>
              <li>Estimated time remaining</li>
              <li>Error log for any failed images</li>
            </ul>
            
            <h4>Resume Capability</h4>
            <p>If processing is interrupted, you can resume from where it stopped. SciPathJ tracks which images have been processed and skips them on restart.</p>
          `
        }
      ]
    },
    {
      title: 'Results & Visualization',
      sections: [
        {
          id: 'data-output',
          title: 'Data Output & Visualization',
          content: `
            <h3>Overview</h3>
            <p>SciPathJ provides several tools to visualize and export the analysis results. These can be accessed from the bottom toolbar of the main interface.</p>
            
            <h4>1. Extracted Features</h4>
            <p>The Features window displays a comprehensive table of all measurements calculated for every detected object (Cell, Nucleus, Cytoplasm, Vessel).</p>
            
            <div class="gui-image-container">
              <img src="https://lh3.googleusercontent.com/d/11raUcEYNlHHod5PR8bG4bf22TD3INKXD" alt="Extracted Features Table" class="docs-image" />
              <p class="image-caption">Extracted Features Table</p>
            </div>
    
            <ul>
              <li><strong>Data Grid:</strong> Shows individual values for each feature (e.g., Area, Circularity, Intensity).</li>
              <li><strong>Navigation:</strong> Use the "Previous" and "Next" buttons to browse through pages of data.</li>
              <li><strong>Export:</strong> Click "Export All Features" to save the complete dataset to a CSV file for external analysis.</li>
            </ul>
    
            <h4>2. ROI Statistics</h4>
            <p>The Statistics window provides a high-level summary of the analysis results for the current image and the entire batch.</p>
            
            <div class="gui-image-container">
              <img src="https://lh3.googleusercontent.com/d/10A9uQ3mq3NLdCRUwP1CgkzemYyGGGSLd" alt="ROI Statistics Summary" class="docs-image" />
              <p class="image-caption">ROI Statistics Summary</p>
            </div>
    
            <ul>
              <li><strong>Counts:</strong> Displays the total number of Vessels, Nuclei, Cytoplasms, and Cells detected.</li>
              <li><strong>Performance:</strong> Shows the analysis time for each image.</li>
              <li><strong>Batch Summary:</strong> At the bottom, you can see the total number of images processed and the average ROIs per image.</li>
              <li><strong>Export:</strong> Save the summary statistics to a CSV file.</li>
            </ul>
    
            <h4>3. Feature Averages</h4>
            <p>The Averages window calculates the mean value of each feature for every ROI type in the image.</p>
            
            <div class="gui-image-container">
              <img src="https://lh3.googleusercontent.com/d/17mqbzFtUclID0G22uZD4Ic0fIJDPA2_x" alt="ROI Feature Averages" class="docs-image" />
              <p class="image-caption">ROI Feature Averages</p>
            </div>
    
            <ul>
              <li><strong>Aggregated Data:</strong> Useful for comparing general characteristics between different images or experimental conditions.</li>
              <li><strong>Grouped by Type:</strong> Averages are calculated separately for Cells, Cytoplasms, Vessels, and Nuclei.</li>
            </ul>
    
            <h4>4. Cluster Visualization</h4>
            <p>The Cluster Colors view visualizes the results of the unsupervised classification (clustering) directly on the image.</p>
            
            <div class="gui-image-container">
              <img src="https://lh3.googleusercontent.com/d/1mDbgrhLKr0Qu_kfVW6Z1n_L9QdieJB_j" alt="Cluster Visualization" class="docs-image" />
              <p class="image-caption">Cluster Visualization Overlay</p>
            </div>
    
            <ul>
              <li><strong>Color-Coded Segments:</strong> Each cell is colored according to its assigned cluster (e.g., Cluster 1 in red, Cluster 2 in cyan).</li>
              <li><strong>Spatial Distribution:</strong> Allows you to easily identify spatial patterns and groupings of similar cells within the tissue.</li>
            </ul>
          `
        },
        {
          id: 'final-analysis',
          title: 'Final Analysis',
          content: `
            <h3>Overview</h3>
            <p>The Final Analysis panel provides summary statistics and comprehensive reporting options.</p>
            
            <h4>Summary Statistics</h4>
            <ul>
              <li><strong>Total Counts:</strong> Number of cells, nuclei, and vessels detected</li>
              <li><strong>Class Distribution:</strong> Percentage breakdown by cell class</li>
              <li><strong>Area Coverage:</strong> Tissue area occupied by each region type</li>
              <li><strong>Density Metrics:</strong> Cells per unit area calculations</li>
            </ul>
            
            <h4>Comparative Analysis</h4>
            <ul>
              <li><strong>Compare Classes:</strong> Statistical comparison between cell types</li>
              <li><strong>Feature Distributions:</strong> Histograms and box plots for each feature</li>
              <li><strong>Correlation Matrix:</strong> Relationships between features</li>
            </ul>
            
            <h4>Report Generation</h4>
            <ul>
              <li><strong>PDF Report:</strong> Generate a formatted analysis report</li>
              <li><strong>Excel Export:</strong> Create spreadsheets with multiple sheets</li>
              <li><strong>Image Montage:</strong> Create figure panels for publication</li>
            </ul>
            
            <h4>Statistical Tests</h4>
            <ul>
              <li><strong>T-test:</strong> Compare means between two groups</li>
              <li><strong>ANOVA:</strong> Compare means across multiple groups</li>
              <li><strong>Correlation Analysis:</strong> Pearson and Spearman correlations</li>
            </ul>
          `
        }
      ]
    },
    {
      title: 'Reference',
      sections: [
        {
          id: 'features-explained',
          title: 'Features Explained',
          content: `
            <h3>ROI Types</h3>
            <p>SciPathJ extracts features from four types of Regions of Interest (ROIs):</p>
            
            <h4>1. Nucleus</h4>
            <p>The nucleus is detected using hematoxylin staining. Features extracted include nuclear size, shape, and staining intensity.</p>
            
            <h4>2. Cytoplasm</h4>
            <p>The cytoplasm region extends from the nucleus boundary. Features include cytoplasmic area, eosin staining intensity, and texture patterns.</p>
            
            <h4>3. Complete Cell</h4>
            <p>The complete cell combines nucleus and cytoplasm. Features represent the entire cell including overall shape and combined staining characteristics.</p>
            
            <h4>4. Vessel</h4>
            <p>Vessels are detected based on their characteristic elongated shape and lumen structure. Features include vessel area, perimeter, and branching patterns.</p>
            
            <h3>Feature Categories</h3>
            <p>SciPathJ extracts a comprehensive set of features for each detected object. These are categorized below:</p>
            
            <h4>Metadata & Identification</h4>
            <table>
              <tr><th>Feature</th><th>Description</th></tr>
              <tr><td>Image Name</td><td>Name of the source image file</td></tr>
              <tr><td>Cell Type</td><td>Type of ROI (Cell, Nucleus, Cytoplasm, Vessel)</td></tr>
              <tr><td>ROI ID</td><td>Unique identifier for the region within the image</td></tr>
              <tr><td>Predicted Class</td><td>Class assigned by the supervised machine learning model</td></tr>
              <tr><td>Confidence</td><td>Confidence score of the prediction</td></tr>
              <tr><td>Cluster</td><td>Cluster ID assigned by unsupervised classification</td></tr>
              <tr><td>ignore</td><td>Flag indicating if the ROI should be excluded from analysis</td></tr>
            </table>

            <table>
              <h4>Morphological Features (Shape & Size)</h4>
              <table>
                <tr><th>Feature</th><th>Description</th></tr>
                <tr><td>area</td><td>Area of selection in square pixels or calibrated units (e.g., µm²).</td></tr>
                <tr><td>perim</td><td>The length of the outside boundary of the selection.</td></tr>
                <tr><td>width</td><td>Width of the smallest rectangle enclosing the selection.</td></tr>
                <tr><td>height</td><td>Height of the smallest rectangle enclosing the selection.</td></tr>
                <tr><td>major</td><td>Length of the primary axis of the best fitting ellipse.</td></tr>
                <tr><td>minor</td><td>Length of the secondary axis of the best fitting ellipse.</td></tr>
                <tr><td>angle</td><td>Angle (0-180 degrees) between the primary axis and a line parallel to the x-axis of the image.</td></tr>
                <tr><td>circ</td><td>Circularity: 4π × Area / Perimeter². A value of 1.0 indicates a perfect circle. As the value approaches 0.0, it indicates an increasingly elongated shape.</td></tr>
                <tr><td>round</td><td>Roundness: 4 × Area / (π × Major_Axis²), or the inverse of the aspect ratio.</td></tr>
                <tr><td>ar</td><td>Aspect Ratio: Major_Axis / Minor_Axis.</td></tr>
                <tr><td>solidity</td><td>Solidity: Area / Convex Area.</td></tr>
                <tr><td>feret</td><td>Feret's Diameter: The longest distance between any two points along the selection boundary (maximum caliper).</td></tr>
                <tr><td>minferet</td><td>Minimum Feret's Diameter: The minimum caliper diameter.</td></tr>
                <tr><td>feretx, ferety</td><td>Starting coordinates of the Feret's diameter.</td></tr>
                <tr><td>feretangle</td><td>Angle (0-180 degrees) of the Feret's diameter.</td></tr>
                <tr><td>bx, by</td><td>Coordinates of the upper left corner of the bounding rectangle.</td></tr>
                <tr><td>x, y</td><td>Centroid: The center point of the selection (average of x and y coordinates of all pixels).</td></tr>
                <tr><td>xm, ym</td><td>Center of Mass: Brightness-weighted average of the x and y coordinates.</td></tr>
              </table>
              
              <h4>Intensity Features (General)</h4>
              <table>
                <tr><th>Feature</th><th>Description</th></tr>
                <tr><td>mean</td><td>Mean Gray Value: Average gray value within the selection.</td></tr>
                <tr><td>median</td><td>The median value of the pixels in the image or selection.</td></tr>
                <tr><td>mode</td><td>Modal Gray Value: Most frequently occurring gray value within the selection.</td></tr>
                <tr><td>min</td><td>Minimum gray value within the selection.</td></tr>
                <tr><td>max</td><td>Maximum gray value within the selection.</td></tr>
                <tr><td>stddev</td><td>Standard Deviation of the gray values used to generate the mean gray value.</td></tr>
                <tr><td>skew</td><td>Skewness: The third order moment about the mean.</td></tr>
                <tr><td>kurt</td><td>Kurtosis: The fourth order moment about the mean.</td></tr>
                <tr><td>intden</td><td>Integrated Density: The product of Area and Mean Gray Value.</td></tr>
              </table>
            <p>These features are calculated specifically for the Hematoxylin (nuclear) and Eosin (cytoplasmic) channels after color deconvolution.</p>
            <table>
              <tr><th>Feature</th><th>Description</th></tr>
              <tr><td>hema_mean, eosin_mean</td><td>Mean intensity for Hematoxylin/Eosin channel</td></tr>
              <tr><td>hema_median, eosin_median</td><td>Median intensity</td></tr>
              <tr><td>hema_mode, eosin_mode</td><td>Mode intensity</td></tr>
              <tr><td>hema_min, eosin_min</td><td>Minimum intensity</td></tr>
              <tr><td>hema_max, eosin_max</td><td>Maximum intensity</td></tr>
              <tr><td>hema_stddev, eosin_stddev</td><td>Standard deviation</td></tr>
              <tr><td>hema_skew, eosin_skew</td><td>Skewness</td></tr>
              <tr><td>hema_kurt, eosin_kurt</td><td>Kurtosis</td></tr>
            </table>
            
            <h4>Spatial Features</h4>
            <table>
              <tr><th>Feature</th><th>Description</th></tr>
              <tr><td>neighbor_count</td><td>Number of neighboring cells within a defined radius</td></tr>
              <tr><td>closest_neighbor_distance</td><td>Distance to the nearest neighboring cell</td></tr>
              <tr><td>vessel_distance</td><td>Distance to the nearest vessel</td></tr>
            </table>
          `
        }
      ]
    }
  ];
  
  let activeSection = $state('introduction');
  
  function scrollToSection(id: string) {
    activeSection = id;
    const element = document.getElementById(id);
    if (element) {
      element.scrollIntoView({ behavior: 'smooth', block: 'start' });
    }
  }
</script>

<svelte:head>
  <title>Documentation - SciPathJ</title>
  <meta name="description" content="Comprehensive documentation for SciPathJ. Learn about installation, segmentation, feature extraction, and cell classification." />
</svelte:head>

<div class="docs-page">
  <!-- Header -->
  <section class="page-header">
    <div class="container">
      <h1>Documentation</h1>
      <p>Complete user guide for SciPathJ</p>
    </div>
  </section>
  
  <!-- Main Content -->
  <div class="docs-container">
    <!-- Sidebar Navigation -->
    <aside class="docs-sidebar">
      <nav class="docs-nav">
        <h3>Contents</h3>
        <div class="nav-categories">
          {#each categories as category}
            <div class="nav-category">
              <h4>{category.title}</h4>
              <ul>
                {#each category.sections as section}
                  <li>
                    <button 
                      class="nav-link" 
                      class:active={activeSection === section.id}
                      onclick={() => scrollToSection(section.id)}>
                      {section.title}
                    </button>
                  </li>
                {/each}
              </ul>
            </div>
          {/each}
        </div>
      </nav>
    </aside>
    
    <!-- Documentation Content -->
    <main class="docs-content">
      {#each categories as category}
        {#each category.sections as section}
          <section id={section.id} class="docs-section">
            <h2>{section.title}</h2>
            {@html section.content}
          </section>
        {/each}
      {/each}
      
      <!-- Help Section -->
      <section class="docs-help">
        <h2>Need More Help?</h2>
        <p>If you can't find what you're looking for in the documentation, here are additional resources:</p>
        <div class="help-links">
          <a href="https://github.com/sebastianmicu24/scipathj/issues" target="_blank" rel="noopener noreferrer" class="btn btn-secondary">
            Open an Issue
          </a>
          <a href="/tutorials" class="btn btn-primary">
            View Tutorials
          </a>
        </div>
      </section>
    </main>
  </div>
</div>

<style>
  .docs-page {
    flex: 1;
  }
  
  /* Page Header */
  .page-header {
    background: linear-gradient(135deg, var(--color-gray-50) 0%, var(--color-white) 100%);
    padding: 3rem 0;
    text-align: center;
    border-bottom: 1px solid var(--color-gray-200);
  }
  
  .page-header h1 {
    color: var(--color-primary);
    margin-bottom: 0.5rem;
  }
  
  .page-header p {
    color: var(--color-gray-600);
    font-size: 1.1rem;
    margin: 0;
  }
  
  /* Docs Container */
  .docs-container {
    display: grid;
    grid-template-columns: 250px 1fr;
    max-width: var(--max-width);
    margin: 0 auto;
    padding: 0 1.5rem;
    gap: 2rem;
  }
  
  /* Sidebar */
  .docs-sidebar {
    position: sticky;
    top: calc(var(--header-height) + 2rem);
    height: fit-content;
    padding: 2rem 0;
    max-height: calc(100vh - var(--header-height) - 4rem);
    overflow-y: auto;
  }
  
  .docs-nav h3 {
    font-size: 0.9rem;
    text-transform: uppercase;
    letter-spacing: 0.05em;
    color: var(--color-gray-500);
    margin-bottom: 1rem;
  }

  .nav-category {
    margin-bottom: 1.5rem;
  }

  .nav-category h4 {
    font-size: 0.85rem;
    font-weight: 600;
    color: var(--color-gray-900);
    margin-bottom: 0.5rem;
    padding-left: 0.75rem;
  }
  
  .docs-nav ul {
    list-style: none;
    padding: 0;
    margin: 0;
  }
  
  .docs-nav li {
    margin-bottom: 0.1rem;
  }
  
  .docs-nav .nav-link {
    display: block;
    width: 100%;
    text-align: left;
    padding: 0.4rem 0.75rem;
    border: none;
    background: none;
    color: var(--color-gray-600);
    font-size: 0.9rem;
    cursor: pointer;
    border-radius: 4px;
    transition: all 0.2s ease;
    border-left: 2px solid transparent;
  }
  
  .docs-nav .nav-link:hover {
    background: var(--color-gray-100);
    color: var(--color-primary);
  }
  
  .docs-nav .nav-link.active {
    background: var(--color-primary-light-10);
    color: var(--color-primary);
    border-left-color: var(--color-primary);
    font-weight: 500;
  }
  
  /* Content */
  .docs-content {
    padding: 2rem 0;
    min-width: 0;
  }
  
  .docs-section {
    margin-bottom: 3rem;
    padding-bottom: 2rem;
    border-bottom: 1px solid var(--color-gray-200);
  }
  
  .docs-section:last-of-type {
    border-bottom: none;
  }
  
  .docs-section h2 {
    color: var(--color-primary);
    margin-bottom: 1.5rem;
    padding-bottom: 0.5rem;
    border-bottom: 2px solid var(--color-primary);
  }
  
  .docs-content :global(h3) {
    color: var(--color-text-primary);
    margin: 1.5rem 0 1rem;
  }
  
  .docs-content :global(h4) {
    color: var(--color-text-primary);
    margin: 1rem 0 0.75rem;
  }
  
  .docs-content :global(p) {
    color: var(--color-text-secondary);
    line-height: 1.7;
    margin-bottom: 1rem;
  }
  
  .docs-content :global(ul), .docs-content :global(ol) {
    color: var(--color-text-secondary);
    margin-bottom: 1rem;
    padding-left: 1.5rem;
  }
  
  .docs-content :global(li) {
    margin-bottom: 0.5rem;
    line-height: 1.6;
  }
  
  .docs-content :global(.warning-box) {
    background: #fff3cd;
    border: 1px solid #ffc107;
    border-radius: 8px;
    padding: 1rem 1.5rem;
    margin: 1rem 0;
  }
  
  .docs-content :global(.warning-box p) {
    margin: 0;
  }
  
  .docs-content :global(table) {
    width: 100%;
    border-collapse: collapse;
    margin: 1rem 0;
  }
  
  .docs-content :global(th), .docs-content :global(td) {
    padding: 0.75rem;
    text-align: left;
    border: 1px solid var(--color-border);
  }
  
  .docs-content :global(th) {
    background: var(--color-bg-tertiary);
    font-weight: 600;
    color: var(--color-text-primary);
  }
  
  .docs-content :global(td) {
    color: var(--color-text-secondary);
  }
  
  .docs-content :global(a) {
    color: var(--color-primary-light);
  }
  
  .docs-content :global(a:hover) {
    text-decoration: underline;
  }

  .docs-content :global(.gui-image-container) {
    margin: 2rem 0;
    text-align: center;
  }
  
  .docs-content :global(.docs-image) {
    max-width: 100%;
    height: auto;
    border-radius: 8px;
    box-shadow: 0 4px 12px rgba(0,0,0,0.1);
    border: 1px solid var(--color-gray-200);
  }
  
  .docs-content :global(.image-caption) {
    margin-top: 0.5rem;
    font-size: 0.9rem;
    color: var(--color-gray-500);
    font-style: italic;
  }
  
  .docs-content :global(em) {
    font-style: italic;
  }
  
  /* Help Section */
  .docs-help {
    background: var(--color-gray-100);
    padding: 2rem;
    border-radius: 8px;
    text-align: center;
    margin-top: 2rem;
  }
  
  .docs-help h2 {
    color: var(--color-gray-900);
    border: none;
    padding: 0;
    margin-bottom: 1rem;
  }
  
  .docs-help p {
    color: var(--color-gray-600);
    margin-bottom: 1.5rem;
  }
  
  .help-links {
    display: flex;
    gap: 1rem;
    justify-content: center;
    flex-wrap: wrap;
  }
  
  /* Responsive */
  @media (max-width: 992px) {
    .docs-container {
      grid-template-columns: 1fr;
    }
    
    .docs-sidebar {
      position: relative;
      top: 0;
      padding: 1rem 0;
      border-bottom: 1px solid var(--color-gray-200);
      max-height: none;
    }
    
    .docs-nav ul {
      display: flex;
      flex-wrap: wrap;
      gap: 0.5rem;
    }
    
    .docs-nav li {
      margin-bottom: 0;
    }
    
    .docs-nav .nav-link {
      padding: 0.5rem 1rem;
    }
  }
  
  @media (max-width: 576px) {
    .docs-nav ul {
      flex-direction: column;
    }
    
    .docs-nav .nav-link {
      width: 100%;
    }
  }
</style>