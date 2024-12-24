# DATASET DESCRIPTION

Here we describe our `dataset.csv` which is found [here]() and how we generated it from pairwise comparisons between open source projects, where the weights are derived from their relative funding amounts.
We also describe which columns are present in the dataset and what is the meaning of each columns and its formats.

## Data Sources

- Project funding data from OSO's BigQuery tables (oss_funding_v0)
- Repository information from OSO's BigQuery tables (repositories_v0)
- Initial dependency graph containing repository URLs (unweighted_graph.json)

## Process

1. **Data Collection**: For each project in our dependency graph, we collected:

- Quarterly funding amounts
- Funder information
- Associated GitHub repository URLs (using the most starred repo when multiple exist)

2. **Comparison Generation**: For each funding round (defined by funder + quarter):

- Found all projects that received funding in that round
- Generated all possible pairs of projects
- Calculated relative weights based on funding amounts

weight_a = amount_a / (amount_a + amount_b)
weight_b = amount_b / (amount_a + amount_b)

3. **Data Consistency**:

- Project pairs are always stored with alphabetically larger URL as project_a
- When the same pair appears in multiple rounds, weights are averaged
- Weights for each pair sum to 1.0

## Output Format

The final CSV contains five columns:

- id: Unique id per pair of GitHub repositories
- project_a: GitHub repository URL (alphabetically larger)
- project_b: GitHub repository URL (alphabetically smaller)
- weight_a: Average relative funding weight for project_a
- weight_b: Average relative funding weight for project_b

## Key Assumptions

- Projects are identified by their GitHub repository URLs
- For projects with multiple repositories, we use the most starred one
- Projects must appear in the same funding round to be compared
- Funding amounts within the same quarter are treated equally (no time-based weighting)
- All funding currencies are converted to USD

## Example

If Project A received $75 and Project B received $25 in a funding round:

```
{
"project_a": "https://github.com/projectA",
"project_b": "https://github.com/projectB",
"weight_a": 0.75, # (75/100)
"weight_b": 0.25 # (25/100)
}
```
