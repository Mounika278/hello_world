import sys
from setuptools import find_packages, setup
from pathlib import Path

CURRENT_DIR = Path(file).parent
sys.path.insert(0, str(CURRENT_DIR))

def get_long_description() -> str:
      return (
            (CURRENT_DIR / "python.md").read_text(encoding="utf8")
      )

setup(name='PythonLoginAndRegister',
      version='0.1',
      description='Basic Login and Registration in Python',
      long_description=get_long_description(),
      url:https://coda.io/d/_dH_9CwhSTfy/BRD-for-Corporate-Insurance-Market-Place_suouP
      author='coda.io',
      author_email='mounikasoft529@gmail.com',
      license='MIT',
      packages=['PythonLoginAndRegister'],
      package_dir={"PythonLoginAndRegister": "src"},
      zip_safe=False)

    
        
