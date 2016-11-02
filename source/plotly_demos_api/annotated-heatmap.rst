#################
annotated-heatmap
#################

https://plot.ly/python/annotated\_heatmap/

.. contents:: `Contents`
   :depth: 2
   :local:


Simple annotated heatmp
=======================

.. code:: python

    import plotly.plotly as py
    from plotly.tools import FigureFactory as FF
    
    z = [[.1, .3, .5, .7, .9],  
         [1, .8, .6, .4, .2],
         [.2, 0, .5, .7, .9],  
         [.9, .8, .4, .2, 0],
         [.3, .4, .5, .7, 1]] 
    
    fig = FF.create_annotated_heatmap(z)
    py.iplot(fig)




.. raw:: html

    <iframe id="igraph" scrolling="no" style="border:none;" seamless="seamless" src="https://plot.ly/~takanori/577.embed" height="525px" width="100%"></iframe>



Defined Colorscale
==================

.. code:: python

    import plotly.plotly as py
    from plotly.tools import FigureFactory as FF
    
    z = [[.1, .3, .5, .7],  
         [1, .8, .6, .4],
         [.6, .4, .2, .0],  
         [.9, .7, .5, .3]] 
    
    fig = FF.create_annotated_heatmap(z, colorscale='Viridis')
    py.iplot(fig)





.. raw:: html

    <iframe id="igraph" scrolling="no" style="border:none;" seamless="seamless" src="https://plot.ly/~takanori/579.embed" height="525px" width="100%"></iframe>



Custom Colorscale
=================

.. code:: python

    import plotly.plotly as py
    from plotly.tools import FigureFactory as FF
    
    z = [[.1, .3, .5, .7],  
         [1.0, .8, .6, .4],
         [.6, .4, .2, 0.0],  
         [.9, .7, .5, .3]] 
    
    colorscale = [[0, '#66475e'], [1, '#ecbfe0']]
    font_colors = ['#efecee', '#3c3636']
    fig = FF.create_annotated_heatmap(z, colorscale=colorscale, font_colors=font_colors)
    py.iplot(fig)




.. raw:: html

    <iframe id="igraph" scrolling="no" style="border:none;" seamless="seamless" src="https://plot.ly/~takanori/581.embed" height="525px" width="100%"></iframe>



Custom Text and X & Y Labels
============================

.. code:: python

    z = [[.1, .3, .5],  
         [1.0, .8, .6],
         [.6, .4, .2]]
    
    x = ['Team A', 'Team B', 'Team C']
    y = ['Game Three', 'Game Two', 'Game One']
    
    z_text = [['Win', 'Lose', 'Win'],  
              ['Lose', 'Lose', 'Win'],
              ['Win', 'Win', 'Lose']]
    
    fig = FF.create_annotated_heatmap(z, x=x, y=y, annotation_text=z_text, colorscale='Viridis')
    py.iplot(fig)




.. raw:: html

    <iframe id="igraph" scrolling="no" style="border:none;" seamless="seamless" src="https://plot.ly/~takanori/583.embed" height="525px" width="100%"></iframe>



Annotated Heatmap with numpy
============================

.. code:: python

    import numpy as np
    
    z = np.random.randn(20, 20)
    z_text = np.around(z, decimals=2) # Only show rounded value (full value on hover)
    
    fig = FF.create_annotated_heatmap(z, annotation_text=z_text, colorscale='Greys', hoverinfo='z')
    
    # Make text size smaller
    for i in range(len(fig.layout.annotations)):
        fig.layout.annotations[i].font.size = 8
        
    py.iplot(fig)




.. raw:: html

    <iframe id="igraph" scrolling="no" style="border:none;" seamless="seamless" src="https://plot.ly/~takanori/585.embed" height="525px" width="100%"></iframe>



Custom Hovertext
================

.. code:: python

    # Add Periodic Table Data
    symbol = [['H', '', '', '', '', '', '', '', '', '', '', '', '', '', '', '', '', 'He'],
             ['Li', 'Be', '', '', '', '', '', '', '', '', '', '', 'B', 'C', 'N', 'O', 'F', 'Ne'],
             ['Na', 'Mg', '', '', '', '', '', '', '', '', '', '', 'Al', 'Si', 'P', 'S', 'Cl', 'Ar'],
             ['K', 'Ca', 'Sc', 'Ti', 'V', 'Cr', 'Mn', 'Fe', 'Co', 'Ni', 'Cu', 'Zn', 'Ga', 'Ge', 'As', 'Se', 'Br', 'Kr'],
             ['Rb ', 'Sr', 'Y', 'Zr', 'Nb', 'Mo', 'Tc', 'Ru', 'Rh', 'Pd', 'Ag', 'Cd', 'In', 'Sn', 'Sb', 'Te', 'I', 'Xe' ],
             ['Cs', 'Ba', '', 'Hf', 'Ta', 'W', 'Re', 'Os', 'Ir', 'Pt', 'Au', 'Hg', 'Tl', 'Pb', 'Bi', 'Po', 'At', 'Rn' ],
             ['Fr', 'Ra', '', 'Rf', 'Db', 'Sg', 'Bh', 'Hs', 'Mt', 'Ds', 'Rg', 'Cn', 'Uut', 'Fl', 'Uup', 'Lv', 'Uus', 'Uuo'],
             ['', '', 'La', 'Ce', 'Pr', 'Nd', 'Pm', 'Sm', 'Eu', 'Gd', 'Tb', 'Dy', 'Ho', 'Er', 'Tm', 'Yb', 'Lu', ''],
             ['', '', 'Ac', 'Th', 'Pa', 'U', 'Np', 'Pu', 'Am', 'Cm', 'Bk', 'Cf', 'Es', 'Fm', 'Md', 'No', 'Lr', '' ],
             ['', '', '', '', '', '', '', '', '', '', '', '', '', '', '', '', '', ''],
             ['', 'Alkali Metal', '', '', 'Transition Metal', '', '', 'Actinide', '', '', 'Semimetal', '', '', 'Halogen', '', '', '', ''],
             ['', 'Alkaline Metal', '', '', 'Lanthanide', '', '', 'Basic Metal', '', '', 'Nonmetal', '', '', 'Noble Gas', '', '', '', '']]
    
    element = [['Hydrogen', '', '', '', '', '', '', '', '', '', '', '', '', '', '', '', '', 'Helium'],
               ['Lithium', 'Beryllium', '', '', '', '', '', '', '', '', '', '', 'Boron', 'Carbon', 'Nitrogen', 'Oxygen', 'Fluorine', 'Neon'],
               ['Sodium', 'Magnesium', '', '', '', '', '', '', '', '', '', '', 'Aluminium', 'Silicon', 'Phosphorus', 'Sulfur', 'Chlorine', ' Argon'],
               ['Potassium', ' Calcium', ' Scandium', ' Titanium', ' Vanadium', ' Chromium',  'Manganese', 'Iron', 'Cobalt', 'Nickel', 'Copper', 'Zinc', 'Gallium', 'Germanium', 'Arsenic', 'Selenium', 'Bromine', 'Krypton'],
               ['Rubidium', 'Strontium', 'Yttrium', 'Zirconium', 'Niobium', 'Molybdenum', 'Technetium', 'Ruthenium', 'Rhodium', 'Palladium', 'Silver', 'Cadmium', 'Indium', 'Tin', 'Antimony', 'Tellurium', 'Iodine', 'Xenon'],
               [' Cesium', ' Barium', '',  'Hafnium', 'Tantalum', 'Tungsten', 'Rhenium', 'Osmium', 'Iridium', 'Platinum', 'Gold', 'Mercury', 'Thallium', 'Lead', 'Bismuth', 'Polonium', 'Astatine', 'Radon'],
               [' Francium', ' Radium', '', 'Rutherfordium','Dubnium','Seaborgium','Bohrium','Hassium','Meitnerium','Darmstadtium','Roentgenium','Copernicium','Ununtrium','Ununquadium','Ununpentium','Ununhexium','Ununseptium','Ununoctium'],
               ['', '',  'Lanthanum', 'Cerium', 'Praseodymium', 'Neodymium', 'Promethium', 'Samarium', 'Europium', 'Gadolinium', 'Terbium', 'Dysprosium', 'Holmium', 'Erbium', 'Thulium', 'Ytterbium', 'Lutetium', ''],
               ['', '', 'Actinium', 'Thorium', 'Protactinium', 'Uranium', 'Neptunium', 'Plutonium', 'Americium', 'Curium', 'Berkelium', 'Californium', 'Einsteinium','Fermium' ,'Mendelevium', 'Nobelium', 'Lawrencium', '' ],
               ['', '', '', '', '', '', '', '', '', '', '', '', '', '', '', '', '', ''],
               ['', '', '', '', '', '', '', '', '', '', '', '', '', '', '', '', '', ''],
               ['', '', '', '', '', '', '', '', '', '', '', '', '', '', '', '', '', '']]
    
    atomic_mass = [[ 1.00794, .0, .0, .0, .0, .0, .0, .0, .0, .0, .0, .0, .0, .0, .0, .0, .0,  4.002602],
         [ 6.941, 9.012182, .0, .0, .0, .0, .0, .0, .0, .0, .0, .0,  10.811, 12.0107, 14.0067, 15.9994, 18.9984032, 20.1797],
         [ 22.98976928, 24.3050, .0, .0, .0, .0, .0, .0, .0, .0, .0, .0,  26.9815386, 28.0855, 30.973762, 32.065, 35.453, 39.948], 
         [ 39.0983, 40.078, 44.955912, 47.867, 50.9415, 51.9961, 54.938045, 55.845, 58.933195, 58.6934, 63.546, 65.38, 69.723, 72.64, 74.92160, 78.96, 79.904, 83.798],
         [ 85.4678, 87.62, 88.90585, 91.224, 92.90638, 95.96, 98, 101.07, 102.90550, 106.42, 107.8682, 112.411, 114.818, 118.710, 121.760, 127.60, 126.90447, 131.293],
         [ 132.9054519, 137.327, .0, 178.49, 180.94788, 183.84, 186.207, 190.23, 192.217, 195.084, 196.966569, 200.59, 204.3833, 207.2, 208.98040, 209, 210, 222],
         [223, 226, .0, 267, 268, 271, 272, 270, 276, 281, 280, 285, 284, 289, 288, 293, 'unknown', 294],
         [.0, .0, 138.90547, 140.116, 140.90765, 144.242, 145, 150.36, 151.964, 157.25, 158.92535, 162.500, 164.93032, 167.259, 168.93421, 173.054, 174.9668, .0],
         [.0, .0, 227, 232.03806, 231.03588, 238.02891, 237, 244, 243, 247, 247, 251, 252, 257, 258, 259, 262, .0],
         [.0, .0, .0, .0, .0, .0, .0, .0, .0, .0, .0, .0, .0, .0, .0, .0, .0, .0],
         [.0, .0, .0, .0, .0, .0, .0, .0, .0, .0, .0, .0, .0, .0, .0, .0, .0, .0],
         [.0, .0, .0, .0, .0, .0, .0, .0, .0, .0, .0, .0, .0, .0, .0, .0, .0, .0]]
    
    z = [[.8, .0, .0, .0, .0, .0, .0, .0, .0, .0, .0, .0, .0, .0, .0, .0, .0, 1.],
         [.1, .2, .0, .0, .0, .0, .0, .0, .0, .0, .0, .0, .7, .8, .8, .8, .9, 1.],
         [.1, .2, .0, .0, .0, .0, .0, .0, .0, .0, .0, .0, .6, .7, .8, .8, .9, 1], 
         [.1, .2, .3, .3, .3, .3, .3, .3, .3, .3, .3, .3, .6, .7, .8, .8, .9, 1.],
         [.1, .2, .3, .3, .3, .3, .3, .3, .3, .3, .3, .3, .6, .6, .7, .7, .9, 1.],
         [.1, .2, .4, .3, .3, .3, .3, .3, .3, .3, .3, .3, .6, .6, .6, .7, .9, 1.],
         [.1, .2, .5, .3, .3, .3, .3, .3, .3, .3, .3, .3, .6, .6, .6, .6, .9, 1.],
         [.0, .0, .4, .4, .4, .4, .4, .4, .4, .4, .4, .4, .4, .4, .4, .4, .4, .0],
         [.0, .0, .5, .5, .5, .5, .5, .5, .5, .5, .5, .5, .5, .5, .5, .5, .5, .0],
         [.0, .0, .0, .0, .0, .0, .0, .0, .0, .0, .0, .0, .0, .0, .0, .0, .0, .0],
         [.1, .1, .1, .3, .3, .3, .5, .5, .5, .7, .7, .7, .9, .9, .9, .0, .0, .0],
         [.2, .2, .2, .4, .4, .4, .6, .6, .6, .8, .8, .8, 1., 1., 1., .0, .0, .0]]
    
    # Display element name and atomic mass on hover
    hover=range(len(symbol))
    for x in range(len(symbol)):
        hover[x] = [i + '<br>' + 'Atomic Mass: ' + str(j) for i, j in zip(element[x], atomic_mass[x])]
    
    # Invert Matrices
    symbol = symbol[::-1]
    hover = hover[::-1]
    z = z[::-1]
    
    # Set Colorscale
    colorscale=[[0.0, 'rgb(255,255,255)'], [.2, 'rgb(255, 255, 153)'], 
                [.4, 'rgb(153, 255, 204)'], [.6, 'rgb(179, 217, 255)'], 
                [.8, 'rgb(240, 179, 255)'],[1.0, 'rgb(255, 77, 148)']]
    
    # Make Annotated Heatmap
    pt = FF.create_annotated_heatmap(z, annotation_text=symbol, text=hover,
                                     colorscale=colorscale, font_colors=['black'], hoverinfo='text')
    pt.layout.title = 'Periodic Table'
    
    py.iplot(pt)




.. raw:: html

    <iframe id="igraph" scrolling="no" style="border:none;" seamless="seamless" src="https://plot.ly/~takanori/587.embed" height="525px" width="100%"></iframe>



