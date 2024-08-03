# NBA Analysis Projects

Welcome to my GitHub repository dedicated to comprehensive NBA analysis! This repository contains multiple projects, each focusing on different aspects of NBA player statistics and trends. Below, you will find detailed descriptions of the projects along with links to the analysis files, relevant code snippets and visualizations. Dive in to explore the fascinating world of NBA analytics! 
<br>
<br>
## Projects Overview

### 1. Determinants of NBA Players' Career Length - Statistical Analysis
This project includes a detailed description of the data used for model building and the process of constructing and evaluating the statistical model. These data encompass a variety of variables concerning NBA players, such as game statistics, physical characteristics, and other factors that may influence the length of their careers. \
The model building process began with data preparation, which involved cleaning and transforming the data into the appropriate format. An exploratory data analysis was then conducted to understand the structure of the data and identify potential significant variables. Linear regression techniques were used to build a basic model and assess the linear impact of variables on the players' career length. However, to better capture the nonlinear relationships between variables, nonlinear models were also applied. \
In the further part of the study, advanced machine learning techniques were employed, including decision trees, random forests, and the k-nearest neighbors method. These models allowed for more comprehensive data analysis and better prediction of NBA players' career length. Each model was meticulously evaluated for effectiveness using appropriate evaluation metrics such as R^2, mean squared error (MSE), and other statistical measures. \
The impact of individual variables on the career length of NBA players was analyzed, enabling the identification of the most important factors. The results of the analysis were interpreted, highlighting the significance of particular variables and their potential importance in the context of managing players' careers and NBA team strategies.
<br>
<br>
#### Analysis Files
- [NBA players'career length analysis](https://github.com/GrzegorzPus/NBA_analysis/blob/main/NBA%20players'%20career%20lengths.ipynb) - This file contains the detailed analysis of the determinants affecting the length of NBA careers.
<br>

#### Key Findings
Some of the key determinants analyzed include:
- **Player Performance Metrics**: Points per game, assists, rebounds, etc.
- **Non-Basketball Factors**: Age, height, weight and nationality.
<br>

#### Sample Code
```python
plt.figure(figsize=(16,7))
sns.residplot(x=np.arange(len(model.resid)), y=model.resid, lowess=False, color="g")
plt.title('Chart of residuals')
plt.xlabel('Number of observation')
plt.ylabel('Residuals')
plt.show()

white_test = het_white(model.resid, X)
p_value = white_test[1]

print(f'P-value: {p_value}')

alpha = 0.05
if p_value > alpha:
    print('There is no significant evidence of heteroskedasticity in the residuals')
else:
    print('Significant evidence of heteroskedasticity in the residuals was detected')
```
You can read a deeper analysis with all the visualisations, descriptions and conclusions in the project above.
<br>
<br>

### 2. Analysis of NBA Player Heights
Height is a crucial factor in basketball, influencing a player's position and role on the team. This project examines the distribution of player heights and how they have evolved over time. \
Our analysis delves into the evolution of the average height of NBA players across different eras, identifying observable trends and patterns. This section specifically concentrates on how the typical height for each position—guard, forward, and center—has transformed over the years. We examine the implications of these height changes for team strategies and player roles within the league. \
By scrutinizing historical data, we can observe significant shifts in the physical profiles of players occupying different positions. For instance, guards have not only become taller but also more versatile, impacting the dynamics of backcourt play. Forwards have evolved in both height and skill set, reflecting the modern game's demands for multi-functional players who can stretch the floor. Centers, traditionally the tallest players on the court, have seen variations in average height corresponding with changes in playing style, such as the increased emphasis on perimeter shooting and agility. \
These height trends are not merely statistical curiosities; they have profound implications for how teams construct their rosters and devise their strategies. Taller guards might suggest a shift towards a more defensively robust and versatile backcourt, while the evolving role of forwards indicates a need for players who can adapt to multiple positions and responsibilities. The changing profile of centers underscores the ongoing transition from traditional post play to a more dynamic, perimeter-oriented approach.
<br>
<br>
#### Analysis Files
- [Height and weight](https://github.com/GrzegorzPus/NBA_analysis/blob/main/Height%20and%20weight.ipynb)
<br>

#### Key Findings
- **Guards**: there has been an increase in average height along with greater versatility and defensive skills, significantly impacting the dynamics of backcourt play
- **Forwards**: have evolved in both height and skill set, reflecting the modern game's demand for multi-functional players capable of adapting to various roles and extending play to the perimeter
- **Centers**: have experienced changes in average height corresponding with a shift from traditional post play to a more dynamic, perimeter-oriented style, emphasizing mobility and shooting abilities
<br>

#### Sample Code
```python
fig, axs = plt.subplots(2, 3, figsize=(16, 9), sharex=True)

def plot_average_weight(ax, df, position_name):
    average_weight_by_year = df.groupby('draft_year')['weight_kg'].mean().reset_index()
    ax.plot(average_weight_by_year['draft_year'], average_weight_by_year['weight_kg'], marker='o')
    ax.set_title(position_name, fontsize=14, fontweight='bold')
    ax.tick_params(axis='x', rotation=90)
    ax.grid(False)

plot_average_weight(axs[0, 0], df_PG, 'Point Guard')
plot_average_weight(axs[0, 1], df_SG, 'Shooting Guard')
plot_average_weight(axs[1, 0], df_SF, 'Small Forward')
plot_average_weight(axs[1, 1], df_PF, 'Power Forward')
plot_average_weight(axs[1, 2], df_C, 'Center')
axs[0, 2].axis('off')

x_ticks = average_weight_by_year5['draft_year'][::6]
x_ticks = [int(x) for x in x_ticks if not pd.isna(x)]
plt.xticks(x_ticks)
plt.suptitle('The Average Weight Depending on the Draft Year by Position', fontsize=18, fontweight='bold')
fig.text(0, 0.5, 'Average weight [kg]', va='center', rotation='vertical', fontsize=12, fontweight='bold')

plt.tight_layout()
plt.show()
```
You can read a deeper analysis with all the visualisations, descriptions and conclusions in the project above.
