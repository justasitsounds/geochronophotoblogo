# Map Generation

## populated places

### Basic country outlines for Americas
    
    ogr2ogr -f GeoJSON -where "region_un = 'Americas'"  americas.json ~/Downloads/110m_cultural/ne_110m_admin_0_countries_lakes.shp
    
### Countries/Provinces

USA States:
    
    ogr2ogr -f GeoJSON -where "iso_a2 = 'US' AND type='State'"  american_states.json ~/Downloads/110m_cultural/ne_110m_admin_1_states_provinces_lakes_shp.shp

Then altered the GeoJSON dataset by changing the 'name' key of each state to 'su_a3' so that it is pulled out the id property in the next transformation
    
    sed -i '.bak' 's/name"/su_a3/g' new_world.json
    
## Combining datatsets

    topojson -o new_world.json --id-property su_a3 --properties name=NAME -- americas.json american_states.json

---
# Site Layout

## Mobile (first)

### Portrait

    ==================
    | date slider    |
    -----------------|
    | Mini Map       |
    |                |
    -----------------| 
    |                |
    | Content/Photos |
    |                |
    |                |
    |                |
    |                |
    ==================

Date slider and map stay put, Content/Photos scroll. Date slider/Map update as user scrolls. Map and Date slider allow navigation - content jumps.

### Landscape/Tablet

    =================================
    |        date slider            |
    --------------------------------|
    |                   |           |
    |   Content/Photos  | Map       |
    |                   |           |
    |                   |           |
    =================================
   

