  runs-on: ubuntu-latest
    env:
      PYTHON: ${{ matrix.python-version }}
      KERAS_BACKEND: ${{ matrix.backend }}
      KERAS_HOME: .github/workflows/config/${{ matrix.backend }}
    steps:
      - uses: actions/checkout@v3
      - name: Check for changes in keras/applications
@@ -59,7 +59,7 @@ jobs:
        if: ${{ steps.filter.outputs.applications == 'true' }}
        uses: codecov/codecov-action@v3
        with:
          env_vars: PYTHON,KERAS_BACKEND
          env_vars: PYTHON,KERAS_HOME
          flags: keras.applications,keras.applications-${{ matrix.backend }}
          files: apps-coverage.xml
          fail_ci_if_error: false
@@ -82,7 +82,7 @@ jobs:
      - name: Codecov keras
        uses: codecov/codecov-action@v3
        with:
          env_vars: PYTHON,KERAS_BACKEND
          env_vars: PYTHON,KERAS_HOME
          flags: keras,keras-${{ matrix.backend }}
          files: core-coverage.xml
          fail_ci_if_error: false
 6 changes: 6 additions & 0 deletions6  
.github/workflows/config/jax/keras.json
@@ -0,0 +1,6 @@
{
    "floatx": "float32",
    "epsilon": 1e-07,
    "backend": "jax",
    "image_data_format": "channels_last"
}
 6 changes: 6 additions & 0 deletions6  
.github/workflows/config/numpy/keras.json
@@ -0,0 +1,6 @@
{
    "floatx": "float32",
    "epsilon": 1e-07,
    "backend": "numpy",
    "image_data_format": "channels_last"
}
 6 changes: 6 additions & 0 deletions6  
.github/workflows/config/tensorflow/keras.json
@@ -0,0 +1,6 @@
{
    "floatx": "float32",
    "epsilon": 1e-07,
    "backend": "tensorflow",
    "image_data_format": "channels_last"
}
 6 changes: 6 additions & 0 deletions6  
.github/workflows/config/torch/keras.json
@@ -0,0 +1,6 @@
{
    "floatx": "float32",
    "epsilon": 1e-07,
    "backend": "torch",
    "image_data_format": "channels_first"
