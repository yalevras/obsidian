
How cameras are made (14 variations)
Space Lab Tech want a camera withotu a lens. In thermal testing, may reglect something differently, there are disturbances. Every change has inintended consequences

Product
- existing assembly drawing
- MRS (manufacturing how to assembly something)
- test procedures
- a test plan overarches a test procedure
do these AI&T
doing documentation the whole way along
hold a TRR (test readyness review)
MRB (material review board) + NCR (if something is wrong, missing a part, a hole is not where a hole should be, threads are wrong)
there is a currrent 5 month long mrb for the camera the space lab test one

2 mono 2 colour, cameras in a box to monitor how plants grow, artemis 4
connector on the side for data and power on the nisa camera, it is not a perfect seal and lets light in

after every test, we turn the camera on and see that its working, we ned to document between each testing stage.

we're taking 4-6 months to get a camera to a custome

2 EMS and 4 FMS

at the end of the thing (EIDP (end item data package)), where they say that a thing was inspected
ours:
- information about serial number of unit
- what tests happened
- sometimes will give copy of test recards
- sometimes will give data summary
- graphs etc showing vibe levels and temperature profiles
- the customer is paying for all of this, this is all of what we give to them
- material records
	- type of mateirals used, aluminum 77, what lot (who did you buy it from)
	- fastener
- AD-AB comparison (as designed, as built)

jake jordan luke daniel anne

research automation for this type of test that already exists

eidp will be 80% the same each time
nrc and mrb will be different each time.

end goal is to minimize time

we get paid when [HWSW] + [Documentation] = $

in the camera
2 boards, mounting thehboards together
programming the board


Custom

is there someway where we can use automatino tools, to have a complete set of templates to build a camera end to end. does not have to be ai. maybe python said, insert value turn the camera, did you put in ___ blank volts. where we can populate data.



when we need to change something like a hole or something
we do a comparison for the customer of, as designed, and as built. maybe the next hole will let light in. maybe it will matter structurly.




Optics,
sensors are very very sensitive to small changes that we cannot tell with out eyes

we are trying to make srue the analog from the hole in the camera does not mess up the stuff. the analog is not predictible and responds in different ways and is more difficult than digital to deal with                  





List of Documents





EIDP (End Item Data Package)


[AD1]     CSYS-NISA-MRS-322894 Manufacturing Record Sheet for CSYS-NISA-PN-322890 Serial Number 14305

[AD2]    CSYS-IM3-TP-321838 REV A Vibration Test Procedure, IM3

[AD3]    CANW2000.0 Vibration Testing #14305, 14306, 14307, 14308 NISA Cameras

<mark style="background: #FFF3A3A6;">[AD4]    CSYS-IM3-TP-321839 REV B Ambient Pressure Thermal Test Procedure, IM3</mark>
- includes python scripting for .csv creation and plot making (Section 5.7)
	- what is ThermalLogPlotterCsv.py used for? not seen in documents r thermal test record

<mark style="background: #BBFABBA6;">[AD17] CSYS-NISA-RE-323133 Thermal Test Record for SN 14305 – 14308</mark>
- template - https://www.dropbox.com/scl/fi/qhuypifm5eaguqykjmteh/CSYS-NISA-FO-322384_REV_A_Thermal_Test_Record_Form.xlsx?rlkey=bhjaqc2we1h47zudkudeolif7&st=unl13t2r&dl=0
- on excel main sheet, test software version specified, not sure if this can be autopopulated

[AD5]    CSYS-NISA-PCS-320771 Rev B NISA Burn-in Procedure

<mark style="background: #FFF3A3A6;">[AD6]    CSYS-NISA-TP-321185 Rev C NISA Electrical Testing Procedure</mark>

<mark style="background: #BBFABBA6;">[AD18] CSYS-NISA-TP-320666 Rev B NISA Short Form Functional Test</mark>

[AD7]    CSYS-NISA-RE-323134 Unit 14305 Electrical Function Test Record

[AD8]    CSYS-NISA-PCS-320839 Rev B Edge Response Focusing Process

[AD9]    CSYS-NISA-AI-320665 Rev A Image Circle Verification and Adjustment Procedure

[AD10] CSYS-NISA-TP-320461 Rev A Colour Calibration

[AD11] CSYS-NISA-TP-320710 Rev D NISA Camera Operational Checkout

[AD12] CSYS-NISA-PCS-320771 Rev A NISA Burn-In Procedure

[AD13] CSYS-NISA-RE-323116 Burn-in Record for SN 14305

[AD14] CSYS-NISA-RE-323126 Unit 14305 Post-Vibe Electrical Function Test Record

[AD15] CSYS-NISA-RE-323117 Unit 14305 Pre-Vibe Electrical Function Test Record

[AD16] CSYS-NISA-RE-323125 Vibe Test Record for SN 14305 – 14308 
















