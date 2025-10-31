# Managing Font Sizes on Matplotlib Axes

## Three Types of Text on Axes:

1. **Axis Labels** (e.g., "Average Runs Per Game") - already controlled
2. **Tick Labels** (the numbers/values on the axes) - needs control
3. **Tick Parameters** (rotation, spacing, etc.)

## Methods to Control Font Sizes:

### Method 1: Control Each Axis Separately (Recommended)

```python
# For axis labels (you're already doing this):
axes[0].set_xlabel("Average Runs Per Game", fontsize=10)
axes[0].set_ylabel("Stadium (Home Team)", fontsize=10)

# For tick labels (the numbers):
axes[0].tick_params(axis='x', labelsize=9)  # x-axis tick labels
axes[0].tick_params(axis='y', labelsize=9)  # y-axis tick labels

# Or set both at once:
axes[0].tick_params(labelsize=9)  # both axes
```

### Method 2: Set Tick Label Size Directly

```python
# Get current tick labels and set font size
axes[0].set_xticklabels(axes[0].get_xticklabels(), fontsize=9)
axes[0].set_yticklabels(axes[0].get_yticklabels(), fontsize=9)
```

### Method 3: Global Style (affects all plots)

```python
import matplotlib.pyplot as plt
plt.rcParams['xtick.labelsize'] = 9
plt.rcParams['ytick.labelsize'] = 9
plt.rcParams['axes.labelsize'] = 10
```

## Complete Example for Your Code:

```python
# 2010 visualization
bars_2010 = axes[0].barh(comparison_data_2010.home, comparison_data_2010.runs_2010, color=colors_2010)
axes[0].set_title("2010 Season: Average Runs Per Game by Stadium", fontsize=10, fontweight='bold')
axes[0].set_xlabel("Average Runs Per Game", fontsize=10)
axes[0].set_ylabel("Stadium (Home Team)", fontsize=10)

# Control tick label font sizes
axes[0].tick_params(axis='x', labelsize=9)  # x-axis numbers
axes[0].tick_params(axis='y', labelsize=8)  # y-axis stadium names (smaller for many items)

axes[0].grid(True, alpha=0.3)
```

## Best Practices:

1. **Hierarchy**: Title (largest) > Axis Labels > Tick Labels (smallest)
2. **Readability**: 
   - X-axis tick labels: 9-11pt usually good
   - Y-axis tick labels: 8-10pt (smaller if many items)
   - Axis labels: 10-12pt
3. **For many items** (like 30 stadiums): Use smaller y-axis tick labels (7-8pt)

## Common Font Size Relationships:

```python
# Professional presentation:
title_fontsize = 14
label_fontsize = 11
tick_fontsize = 9

# Compact visualization:
title_fontsize = 10
label_fontsize = 9
tick_fontsize = 8
```

