# Tableau Portifolio - Covid Data Set
This repo highlight some of my skills in using Tableau.
I used SSMS to create some queries/tables that I loaded into Tableau to produce the visuals.
- This dataset came from [ Our world in data ](https://ourworldindata.org/)
- To see the Tableau report in question, please click [here](https://public.tableau.com/app/profile/jay5613/viz/MyPortifolioProject_Covid/Dashboard1?publish=yes)

**Source Code:**
````SQL
---Generate the below tables to use in Tableau Public as couldn't connect direcctly in SQL with the free version
---Code used to generate "Table1" to be used in Tableau
Select SUM(new_cases) as total_cases, SUM(cast(new_deaths as int)) as total_deaths, SUM(cast(new_deaths as int))/SUM(New_Cases)*100 as DeathPercentage
From MyPortifolioProject..Covid_Deaths
where continent is not null 
order by 1,2

--Code used to generate for "Table2" to be used in Tableau
Select location, SUM(cast(new_deaths as int)) as TotalDeathCount
From MyPortifolioProject..Covid_Deaths
Where continent is null 
and location not in ('World', 'European Union', 'International')
Group by location
order by TotalDeathCount desc

---Code used to generate for "Table3" to be used in Tableau
Select Location, Population, MAX(total_cases) as HighestInfectionCount,  Max((total_cases/population))*100 as PercentPopulationInfected
From MyPortifolioProject..Covid_Deaths
Group by Location, Population
order by PercentPopulationInfected desc

---Code used to generate for "Table4" to be used in Tableau
Select Location, Population,date, MAX(total_cases) as HighestInfectionCount,  Max((total_cases/population))*100 as PercentPopulationInfected
From MyPortifolioProject..Covid_Deaths
Group by Location, Population, date
order by PercentPopulationInfected desc
````
*Credits: Alex Freberg youtube channel*
