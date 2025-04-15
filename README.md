# The Analysis

## 1. What are the most demanded skills for the top three most popular data roles?

To fund the most demanded skills for the top 3 moat popular data roles. I filtered out those positions by which ones were the most popular , and got the top 5 skills for thses top 3 roles. This query highlights the most popular job titles and their top skills , showing which skills I should pay attention to depending on the role I'm targeting. 

View my notebook with detailed steps here:

[2_Skill_Demand.ipynb](3_Project\2_Skills_Demand.ipynb)

### Visualize Data

```python
fig, ax = plt.subplots(len(job_titles), 1)

for i, job_title in enumerate(job_titles):
    df_plot = df_skills_perc[df_skills_perc['job_title_short'] == job_title].head(5)
    sns.barplot(data = df_plot,x='skill_percent',y='job_skills',ax=ax[i],hue= 'skill_count',palette='dark:y_r')
    # little cleanup
    ax[i].set_title(job_title)
    ax[i].set_ylabel('')
    ax[i].set_xlabel('')
    ax[i].get_legend().remove()
    ax[i].set_xlim(0, 78)

    # lets add the percentage of job postings in the bar graph for each bar.
    for n, v in enumerate(df_plot['skill_percent']):
        ax[i].text(v + 1, n, f'{v:.0f}%',va='center')
        # n is index and v is value. 
    if i != len(job_titles) - 1:
        ax[i].set_xticks([])

fig.suptitle('Likelihood of Skills Requested in US Job Postings',fontsize=15)
fig.tight_layout(h_pad=0.5) #fix the overlap
plt.show()
```
### Results

![Visualization of Top Skills for Data Nerds](3_Project\images\Skill_demand_all_data_roles.png)

### Insights
- Python is a veratile skill, highly demanded skill across all 3 roles. but most prominently for Data Scientists (72%) and Data Engineers(65%).
- Also , SQL is the most requested skill for the Data Analyst and Data Scientists , with it in over half the job postings for both roles. 