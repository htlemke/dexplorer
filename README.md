# dexplorer

Test project for interactive matplotlib plots (`%matplotlib widget` / ipympl) in RenkuLab sessions.

## Renku setup (once)
The packages in `requirements.txt` are only installed if Renku **builds the session environment from this repository**. A launcher that uses a ready-made image (e.g. "Python Datascience") ignores this file.

1. In the Renku project, add this repository under **Code repositories**: `https://github.com/htlemke/dexplorer`
2. Go to **Sessions → Add session launcher** and choose **Create from code**.
   Select this repository and **JupyterLab** as the frontend.
3. Wait for the image build to finish (a few minutes). Then launch a session.

## Test
Open `plot_test.ipynb` and run all cells:
- **Step 1** lists the installed versions. `ipympl` must not show `NOT INSTALLED`.
- **Step 2** should show a plot with a toolbar that you can pan and zoom.
- **Step 3** should change the curve when you move the slider.

## If the plot does not show
- **The plot is a static picture, or the output is a text line like `Canvas(toolbar=...)`:** the JupyterLab add-on for ipympl isn't loaded. Reload the browser page, then restart the kernel.
- **"Error displaying widget: model not found":** the kernel and JupyterLab use different versions of the widget packages. Check in a terminal with `jupyter labextension list`, which should list `jupyter-matplotlib` and `@jupyter-widgets/jupyterlab-manager`.
- **Quick test in an existing session:** run `pip install ipympl` in a terminal, reload the browser page, then restart the kernel.
