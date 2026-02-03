
/* This ia a program to clean the following dataset and produce a data visualization for my DSI course data visualization module. 
 Ontario Data Catalogue
 https://data.ontario.ca/dataset/school-board-achievements-and-progress
 School board achievements and progress
*/

import excel "C:\Users\CECi\Dropbox\Data Science Course\Module Visualization\Assignment_3\OME_DSB_achievement_ONTDataCatalogue_OCT2025.xlsx", sheet("Unformatted") firstrow

save "C:\Users\CECi\Dropbox\Data Science Course\Module Visualization\Assignment_3\Assignment-3_Stata_dataset.dta"

* Rename credit accumulation by end of G10 variable name
rename CreditAccumulationbytheendo CreditAccumulationG10End

* Rename credit accumulation by end of G10 variable name
rename M CreditAccumulationG11End

* Convert string to numeric
destring CreditAccumulationG10End, gen(CreditAccum_G10) force

* Convert string to numeric
destring CreditAccumulationG11End, gen(CreditAccum_G11) force

* Convert string to numeric
destring FourYearGraduationRate20202, gen(FourYear_GradRate2020) force

* Convert string to numeric
destring FiveYearGraduationRate2019, gen(FiveYear_GradRate2019) force

* Drop rows 73-75
drop in 73/75

* Two scatterplots: Intial view of G10 or G11 benchmark End of Year Credit Accumulation vs. Five Year Graduation Rate
twoway (scatter FiveYear_GradRate2019 CreditAccum_G10) (scatter FiveYear_GradRate2019 CreditAccum_G11) if !missing(FiveYear_GradRate2019), ///
ytitle("Five Year Graduation Rate: 2019-2020 Grade 9 Cohort") ///
xtitle("End of Year Credit Accumulation")

* Specify G10 and G11 scatterplots' respective element characteristics
twoway (scatter FiveYear_GradRate2019 CreditAccum_G10, /// Grade 10 credit accumulation % benchmark
        mcolor(midblue) msymbol(O) msize(medium)) /// Marker color, symbol, size
       (scatter FiveYear_GradRate2019 CreditAccum_G11, /// Grade 11 credit accumulation % benchmark
        mcolor(midgreen) msymbol(D) msize(medium)) /// Marker color, symbol, size
       if !missing(FiveYear_GradRate2019), /// filter for missing results (B29076 and B29041 do not have secondary school panels)
       ytitle("DSB Five-Year Graduation Rate (%)" "2019-2020 Grade 9 Cohort", size(medsmall)) ///
       xtitle("DSB End of Year Benchmark Credit Accumulation (%)" "2023-2024 School Year", size(medsmall)) ///
       legend(order(1 "Grade 10 Credit Accumulation" 2 "Grade 11 Credit Accumulation") ///
              position(6) rows(1) size(medium) region(lcolor(black))) ///
       graphregion(color(white)) plotregion(lcolor(black)) ///
       title("Five-Year Graduation by Credit Accumulation Rates", size(large)) ///
       subtitle("70 Ontario District School Boards, 2019-2020 Grade 9 Cohort", size(medium)) ///
       note("Source: Ontario Open Data - School Board Achievements and Progress" ///
            "data.ontario.ca/dataset/school-board-achievements-and-progress", size(vsmall))

* Format the y and x axis: specify the tick marks to improve readability
* Specify G10 and G11 scatterplots' respective element characteristics
twoway (scatter FiveYear_GradRate2019 CreditAccum_G10, /// Grade 10 credit accumulation % benchmark
        mcolor(midblue) msymbol(O) msize(medium)) /// Marker color, symbol, size
       (scatter FiveYear_GradRate2019 CreditAccum_G11, /// Grade 11 credit accumulation % benchmark
        mcolor(midgreen) msymbol(D) msize(medium)) /// Marker color, symbol, size
       if !missing(FiveYear_GradRate2019), /// filter for missing results (B29076 and B29041 do not have secondary school panels)
       ytitle("DSB Five-Year Graduation Rate" "2019-2020 Grade 9 Cohort", size(medsmall)) /// Use rate terminology in title and on both axis
       xtitle("DSB End of Year Benchmark Credit Accumulation Rate" "2023-2024 School Year", size(medsmall)) ///
	   ylabel(0.65(0.10)1, format(%9.2f) angle(horizontal)) ///  Format tick marks: rate to two decimal places; start at 0.65 on y axis
       xlabel(0.60(0.10)1, format(%9.2f)) ///  Format tick marks: rate to two decimal places; start at 0.60 on axis
       legend(order(1 "Grade 10 Credit Accumulation" 2 "Grade 11 Credit Accumulation") ///
              position(6) rows(1) size(medium) region(lcolor(black))) ///
       graphregion(color(white)) plotregion(lcolor(black)) ///
       title("Five-Year Graduation by Credit Accumulation Rates", size(large)) ///
       subtitle("70 Ontario District School Boards, 2019-2020 Grade 9 Cohort", size(medium)) ///
       note("Source: Ontario Open Data - School Board Achievements and Progress" ///
            "data.ontario.ca/dataset/school-board-achievements-and-progress", size(vsmall))

* Add lowess lines to show trend for both scatterplot sets: Grade 10 and Grade 11
twoway (scatter FiveYear_GradRate2019 CreditAccum_G10, /// Grade 10 credit accumulation % benchmark
        mcolor(midblue) msymbol(O) msize(medium)) /// Marker color, symbol, size
       (lowess FiveYear_GradRate2019 CreditAccum_G10, /// Add G10 lowess line
        lcolor(midblue) lwidth(medium) lpattern(solid)) ///	Line colour, width, pattern	
       (scatter FiveYear_GradRate2019 CreditAccum_G11, /// Grade 11 credit accumulation % benchmark
        mcolor(midgreen) msymbol(D) msize(medium)) /// Marker color, symbol, size
       (lowess FiveYear_GradRate2019 CreditAccum_G11, /// Add G11 lowess line
        lcolor(midgreen) lwidth(medium) lpattern(dash)) /// Line colour, width, pattern
       if !missing(FiveYear_GradRate2019), /// filter for missing results (B29076 and B29041 do not have secondary school panels)
       ytitle("DSB Five-Year Graduation Rate" "2019-2020 Grade 9 Cohort", size(medsmall)) /// Use rate terminology in title and on both axis
       xtitle("DSB End of Year Benchmark Credit Accumulation Rate" "2023-2024 School Year", size(medsmall)) ///
	   ylabel(0.65(0.10)1, format(%9.2f) angle(horizontal)) ///  Format tick marks: rate to two decimal places; start at 0.65 on y axis
       xlabel(0.60(0.10)1, format(%9.2f)) ///  Format tick marks: rate to two decimal places; start at 0.60 on axis
       legend(order(1 "Grade 10 Credit Accumulation" 2 "Grade 11 Credit Accumulation") ///
              position(6) rows(1) size(medium) region(lcolor(black))) ///
       graphregion(color(white)) plotregion(lcolor(black)) ///
       title("Five-Year Graduation by Credit Accumulation Rates", size(large)) ///
       subtitle("70 Ontario District School Boards, 2019-2020 Grade 9 Cohort", size(medium)) ///
       note("Source: Ontario Open Data - School Board Achievements and Progress" ///
            "data.ontario.ca/dataset/school-board-achievements-and-progress", size(vsmall))
		
		
* Add lowess line description to plot legend and improve labeling		
twoway (scatter FiveYear_GradRate2019 CreditAccum_G10, /// Grade 10 credit accumulation % benchmark
        mcolor(midblue) msymbol(O) msize(medium)) /// Marker color, symbol, size
       (lowess FiveYear_GradRate2019 CreditAccum_G10, /// Add G10 lowess line
        lcolor(midblue) lwidth(medium) lpattern(solid)) ///	Line colour, width, pattern	
       (scatter FiveYear_GradRate2019 CreditAccum_G11, /// Grade 11 credit accumulation % benchmark
        mcolor(midgreen) msymbol(D) msize(medium)) /// Marker color, symbol, size
       (lowess FiveYear_GradRate2019 CreditAccum_G11, /// Add G11 lowess line
        lcolor(midgreen) lwidth(medium) lpattern(dash)) /// Line colour, width, pattern
       if !missing(FiveYear_GradRate2019), /// filter for missing results (B29076 and B29041 do not have secondary school panels)
       ytitle("DSB 5-Year Graduation Rate", size(medsmall)) /// Use rate terminology in title and on both axis; remove duplicated information
       xtitle("DSB End-of-Year Benchmark Credit Accumulation Rate, 2023-2024 School Year", size(medsmall)) /// Modify wording for readability
       ylabel(0.65(0.10)1, format(%9.2f) angle(horizontal)) ///  Format tick marks: rate to two decimal places; start at 0.65 on y axis
       xlabel(0.60(0.10)1, format(%9.2f)) ///  Format tick marks: rate to two decimal places; start at 0.60 on axis
       legend(order(1 "Grade 10 Credit Accumulation" 2 "Grade 10 Lowess Trend" /// Add G10 lowess trand line label to legend 
                    3 "Grade 11 Credit Accumulation" 4 "Grade 11 Lowess Trend") /// Add G11 lowess trand line label to legend
              position(6) rows(2) region(lcolor(black))) /// Change legend grid size to two rows
       graphregion(color(white)) plotregion(lcolor(black)) ///
       title("Five-Year Graduation by Credit Accumulation Rates", size(large)) ///
       subtitle("70 Ontario District School Boards, 2019-2020 Grade 9 Graduation Cohort", size(medium)) ///
       note("Source: Ontario Open Data - School Board Achievements and Progress" ///
            "data.ontario.ca/dataset/school-board-achievements-and-progress", size(vsmall)) ///
	   caption("Northwest CDSB & Superior North CDSB omitted: No secondary schools." ///
			"Grade 10 Credit Accumulation Benchmark: 16 or more course credits" ///
			"Grade 11 Credit Accumulation Benchmark: 23 or more course credits", size(vsmall))
		
* Adjust colour scheme to improve colour contrast (hue): try blue/orange contrast, based on WebAIM colour grid, and re-run on https://www.color-blindness.com/coblis-color-blindness-simulator/
* Add lowess line description to plot legend and improve labeling		
twoway (scatter FiveYear_GradRate2019 CreditAccum_G10, /// Grade 10 credit accumulation % benchmark
        mcolor(blue) msymbol(O) msize(medium)) /// Marker color, symbol, size - now blue
       (lowess FiveYear_GradRate2019 CreditAccum_G10, /// Add G10 lowess line
        lcolor(blue) lwidth(medium) lpattern(solid)) ///	Line colour, width, pattern	
       (scatter FiveYear_GradRate2019 CreditAccum_G11, /// Grade 11 credit accumulation % benchmark
        mcolor(orange) msymbol(D) msize(medium)) /// Marker color, symbol, size - now orange
       (lowess FiveYear_GradRate2019 CreditAccum_G11, /// Add G11 lowess line
        lcolor(orange) lwidth(medium) lpattern(dash)) /// Line colour, width, pattern
       if !missing(FiveYear_GradRate2019), /// filter for missing results (B29076 and B29041 do not have secondary school panels)
       ytitle("DSB 5-Year Graduation Rate", size(medsmall)) /// Use rate terminology in title and on both axis; remove duplicated information
       xtitle("DSB End-of-Year Benchmark Credit Accumulation Rate, 2023-2024 School Year", size(medsmall)) /// Modify wording for readability
       ylabel(0.65(0.10)1, format(%9.2f) angle(horizontal)) ///  Format tick marks: rate to two decimal places; start at 0.65 on y axis
       xlabel(0.60(0.10)1, format(%9.2f)) ///  Format tick marks: rate to two decimal places; start at 0.60 on axis
       legend(order(1 "Grade 10 Credit Accumulation" 2 "Grade 10 Lowess Trend" /// Add G10 lowess trand line label to legend 
                    3 "Grade 11 Credit Accumulation" 4 "Grade 11 Lowess Trend") /// Add G11 lowess trand line label to legend
              position(6) rows(2) region(lcolor(black))) /// Change legend grid size to two rows
       graphregion(color(white)) plotregion(lcolor(black)) ///
       title("Five-Year Graduation by Credit Accumulation Rates", size(large)) ///
       subtitle("70 Ontario District School Boards, 2019-2020 Grade 9 Graduation Cohort", size(medium)) ///
       note("Source: Ontario Open Data - School Board Achievements and Progress" ///
            "data.ontario.ca/dataset/school-board-achievements-and-progress", size(vsmall)) ///
	   caption("Northwest CDSB & Superior North CDSB omitted: No secondary schools." ///
			"Grade 10 Credit Accumulation Benchmark: 16 or more course credits" ///
			"Grade 11 Credit Accumulation Benchmark: 23 or more course credits", size(vsmall))	
	
	
* Improve readability: adjust graph margins, simplify legend text amd layout, and expand notes' size
twoway (scatter FiveYear_GradRate2019 CreditAccum_G10, /// Grade 10 credit accumulation % benchmark
        mcolor(blue) msymbol(O) msize(medium)) /// Marker color, symbol, size - now blue
       (lowess FiveYear_GradRate2019 CreditAccum_G10, /// Add G10 lowess line
        lcolor(blue) lwidth(medthick) lpattern(solid)) ///	Line colour, width, pattern	- make trend lines thicker
       (scatter FiveYear_GradRate2019 CreditAccum_G11, /// Grade 11 credit accumulation % benchmark
        mcolor(orange) msymbol(D) msize(medium)) /// Marker color, symbol, size - now orange
       (lowess FiveYear_GradRate2019 CreditAccum_G11, /// Add G11 lowess line
        lcolor(orange) lwidth(medthick) lpattern(dash)) /// Line colour, width, pattern
       if !missing(FiveYear_GradRate2019), /// filter for missing results (B29076 and B29041 do not have secondary school panels)
       ytitle("5-Year Graduation Rate", size(medium)) /// Use rate terminology in title and on both axis; remove duplicated information; increase label size
       xtitle("End-of-Year Credit Accumulation Rate", size(medium)) /// Modify wording for readability ; increase label size
       ylabel(0.65 "65%" 0.75 "75%" 0.85 "85%" 0.95 "95%" 1.00 "100%", ///
              angle(horizontal) grid glcolor(gs14) glwidth(vthin)) /// Add percentage labels and gridlines
       xlabel(0.60 "60%" 0.65 "65%" 0.70 "70%" 0.75 "75%" 0.80 "80%" 0.85 "85%" 0.90 "90%" 0.95 "95%" 1.00 "100%", ///
              grid glcolor(gs14) glwidth(vthin)) /// Add percentage labels and gridlines
       legend(order(1 "Grade 10" 2 "Grade 10 Trend" /// Shorten labels
                    3 "Grade 11" 4 "Grade 11 Trend") ///
              position(6) rows(1) cols(4)  /// Change to single row, keep legend position, specify number of legend columns, 
              size(medsmall) symxsize(5)) /// Change text and symbol sizes; 		  
       graphregion(color(white) margin(medium)) /// Adjust graph region size
       plotregion(lcolor(black) margin(small)) /// Ajust plot region size
       title("Five-Year Graduation by Credit Accumulation Rates", size(large)) ///
       subtitle("70 Ontario District School Boards | 2019-2020 Grade 9 Cohort", size(medium)) ///
       note("Source: Ontario Open Data—School Board Achievements and Progress" ///
            "{it:data.ontario.ca/dataset/school-board-achievements-and-progress}" ///
			" " ///
            "Notes: Northwest CDSB and Superior North CDSB omitted (no secondary schools)." ///
            "Grade 10 benchmark: 16+ credits | Grade 11 benchmark: 23+ credits" /// Make colour grayscale for contrast from main text; add span across note region
			"Cross-sectional, end-of-year credit accumulation rates are for the 2023-2024 school year.", /// Clarify that dataset structure is cross-sectional 
            size(vsmall) color(gs8) span)


