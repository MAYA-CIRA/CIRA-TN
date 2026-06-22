1. Elevation Extraction from ALTM 
DEM Elevation Extractor
#  Merges multiple ALTM DEM tiles (GDAL, memory-safe)
#  Extracts elevation contours at 1m interval
#  Removes negative elevation contours
#  Converts contour lines → filled elevation polygons
#  Outputs: merged DEM, line SHP, polygon SHP, GeoJSON


2. Buffer
SHORELINE BUFFER GENERATOR 
#  Generates 4 land-side buffer shapefiles at 500m intervals (500,1000,1500,2000)
#  Input & Output: Google Drive


3. CIRA_Without_Structures
Inundation Area Identification using Elevation (Shapefile) and Shoreline (Shapefile)
# INPUT: Elevation polygons (shapefile) + Shoreline line (shapefile)
# OUTPUT: Shapefiles only


4. CIRA_WithStructure
Risk Classification Reclassification Based on Sand Dunes and Artificial Structures
# Reads risk rank shapefile(CIRA_Without_Structures) and reclassifies them based on sand dunes and artificial structures
