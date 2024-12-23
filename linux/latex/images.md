We include images by added the package and 
use the corresponding command.

> \usepackage{graphicx}

Then we can use the package

> \includegraphic{image.png}

We can add modification to the image with the optional 
brackets:

```tex
\inludegraphics[width=5cm]{image}
```

We can use relative sizes:

* width = 0.5\textwidth
* height = 0.5\textheight

We can center the image and add caption using the figure argument:

```tex
\begin{figure}
\includegraphic{image}
\centering
\caption{something}
\end{figure}
```
