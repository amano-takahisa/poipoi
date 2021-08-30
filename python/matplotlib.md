# Random color ramp
https://gist.github.com/jgomezdans/402500#gistcomment-2264839
```Python
vals = np.linspace(0,1,256)
np.random.shuffle(vals)
cmap = plt.cm.colors.ListedColormap(plt.cm.jet(vals))
```
