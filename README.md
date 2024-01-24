#matplotlib-challenge

Instructions:
- Prepare the data.
- Generate summary statistics.
- Create bar charts and pie charts.
- Calculate quartiles, find outliers, and create a box plot.
- Create a line plot and a scatter plot.
- Calculate correlation and regression.
- Submit your final analysis.


list of sources used:

- 01: https://pandas.pydata.org/docs/reference/api/pandas.DataFrame.merge.html
- 02: https://saturncloud.io/blog/how-to-find-all-duplicate-rows-in-a-pandas-dataframe/#:~:text=To%20find%20duplicate%20rows%20in%20a%20pandas%20dataframe%2C%20we%20can,get%20all%20the%20duplicate%20rows.
- 03: https://pandas.pydata.org/docs/reference/api/pandas.core.groupby.DataFrameGroupBy.aggregate.html
- 04: bar_chart_solution
- 05: https://saturncloud.io/blog/rotate-tick-labels-in-subplot-using-pyplot-matplotlib-and-gridspec/
- 06: pie_chart_solution
- 07: samples_solution (in 02-Ins-Quartiles_and_Outliers)
- 08:  https://stackoverflow.com/questions/43342564/flier-colors-in-boxplot-with-matplotlib
- 09: correlation_solution
- 10: regression_solution

source 01 was used for merge() to merge two data_frames

    df_combined = pd.merge(mouse_metadata, study_results, how='left', on='Mouse ID')
    merged_df = pd.merge(max_timepoint, clean_df, on=(['Mouse ID','Timepoint']))

source 02 was used to find duplicates using duplicate()

    duplicate_mice = combined_df[combined_df[['Mouse ID', 'Timepoint']].duplicated() == True]

source 03 used the aggregation method with groupby

    agg_drug_summary_df = clean_df.groupby(['Drug Regimen'])[['Tumor Volume (mm3)']].agg(['mean', 'median', 'var', 'std', 'sem'])

source 04 used to plot a bar graph (mostly for formatting)

    plt.bar(x_axis, y_axis, color='blue', alpha=1, align='center')

source 05 for tick rotatin on the x axis

    plt.xticks(rotation=90)

source 06 for pie chart formatting
   
    plt.pie(sizes, labels=labels,autopct="%1.1f%%")

source 07 used for quartile calculations
    
    quartile0 = tumor_vol_data[0].quantile([.25,.5,.75])
    lowerq0 = quartile0[.25]
    upperq0 = quartile0[.75]
    iqr0 = upperq0-lowerq0
    lower_bound0 = lowerq0 - (1.5*iqr0)
    upper_bound0 = upperq0 + (1.5*iqr0)

source 08 for formatting boxplots (specifically marker colors and sizes)

    flierprops = dict(marker='o', markerfacecolor='r', markersize=10, markeredgecolor='black')

source 09 used pearsonr to calculate correlation

    correlation = st.pearsonr(cap_avg_weight,cap_avg_vol)

source 10 to calculate regression values

    (slope, intercept, rvalue, pvalue, stderr) = st.linregress(cap_avg_weight, cap_avg_vol)
    regress_values = cap_avg_weight * slope + intercept
    line_eq = "y = " + str(round(slope,2)) + "x + " + str(round(intercept,2))

note: there were times i had to look through the dataframe to check if it had the correct data and there were also debugging done with adding missing variables or not closing out functions