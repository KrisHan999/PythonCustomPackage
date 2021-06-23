# PythonCustomPackage

This readme file is for git repository, for custom package generation, customize user's own readme (like, README.txt).
Follow `https://the-hitchhikers-guide-to-packaging.readthedocs.io/en/latest/creation.html`, `https://packaging.python.org/tutorials/packaging-projects/` and `https://www.youtube.com/watch?v=zhpI6Yhz9_4&t=265s`.

This is some key points I want to point out:
1. package file structure should be like:
   ```
    ├── LICENSE.txt (MIT license at `https://opensource.org/licenses/MIT`)
    ├── MANIFEST.in (Including files in source distributions with MANIFEST.in. https://packaging.python.org/guides/using-manifest-in/)
    ├── README.txt
    ├── CHANGE.txt (Version change log)
    ├── example_pkg
    │   └── __init__.py
    └── setup.py
   ```  
2. - `long_description_content_type` inside `setup.py`. check `https://packaging.python.org/guides/making-a-pypi-friendly-readme/`. There are three different types, `text/plain`, `text/x-rst` (for reStructuredText), or `text/markdown`. Worth to mention is that if using `text/x-rst`, section head signs like `_`, `=`, should longer than the header text itself.
   
   - `name` inside setup.py should be the folder name (like, example_pkg) which contains the source code. It is also the final package name.
3. create dist using `python setup.py sdist bdist_wheel`. This will generate folders: `build`, `dist`, `xxxx.egg_info`. `wheel` and `zip` file are stored inside `dist` folder.
4. use `twine check dist/*` to check the generated package.
5. use **relative path('.', '..'')** to import module in scripts!!!
6. each module should have a `__init__.py` file
