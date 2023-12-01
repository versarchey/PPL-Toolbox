# Generate QC Report of PPL
## Prepare required files
Before using this module, you need run PPL and generate required files for this steps.      
Their suffixes should be:  
- .contacts (generated by PPL main module)

- .basic_statistics.txt (generated by PPL main module)

- .penalty.distribution (generated by PPL main module)

- .bc (generated by utils.BoundaryCheck )    

- .bc.evenByChr (generated by utils.BoundaryCheck )    

- .dd (generated by utils.StatDimensionDistribution )

- .ii (generated by utils.StatIntraInter)   

respectively. All these files need to be in the PPL output directory. Such as:
<p>
./prefix/  <br>
├── prefix.basic_statistics.txt  <br>
├── prefix.bc   <br>
├── prefix.bc.evenByChr<br>
├── prefix.contacts<br>
├── prefix.dd<br>
├── prefix.ii<br>
└── prefix.penalty.distribution<br>
</p>

The illustration for these functions can be checked on PPL. If you don't want to know it, you just use the code below to generate all information file:

    prefix="test01"

    #generate .dd
    java -cp PPL.jar utils.StatDimensionDistribution $prefix/$prefix.contacts $prefix/$prefix.dd
    #generate .bc .bc.evenByChr
    java -cp PPL.jar utils.BoundaryCheck $prefix/$prefix.contacts $prefix/$prefix.bc
    $generate .ii
    java -cp PPL.jar utils.StatIntraInter $prefix/$prefix.contacts $prefix/$prefix.ii

## Install
Visulazition module is based on Python 3.8.  
Just run `pip install -r requirements.txt`.
Our test environment is on Windows Subsystem Linux Ubuntu.

## Run
    # generate figure (saved in directory "./figs")
    bash plot_png.sh $output_dir $id
    # generate docx file
    python generate_report_docx.py 




