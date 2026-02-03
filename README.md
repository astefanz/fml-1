*Fan-Array Machine Learning 1* - code supplement to:
# Data-driven modelling for on-demand flow prescription in fan-array wind tunnels

See `fml1.ipynb` for code.
Dataset file: `dataset.pickle`.

Data used in *Data-driven modelling for on-demand flow prescription in fan-array wind tunnels*
by Stefan-Zavala et al. (https://doi.org/10.1017/flo.2025.10034) compiled for publication.
All measurements were done indoors on air at standard temperature and pressure (1 atm, 25°C).
The density used to solve for velocity from dynamic pressure is 1.225 kg/m^3.

# Keys:

- `notes_internal`: (`str`) Context used within research group
- `README`: (`str`) Context notes of this dataset.
- `keys_explained`: (`dict`) dict with lookup for the meaning of all keys in this and all sub-dictionaries.
	- `README`: (`str`) Context notes of this dataset.
	- `keys_explained`: (`str`) dict with lookup for the meaning of all keys in this and all sub-dictionaries.
	- `notes_internal`: (`str`) Context used within research group
	- `common`: (`str`) dict containing data and parameters shared across all datasets.
	- `xLs_str`: (`str`) tuple of x/L values (as `str`) used as keys in `data`
	- `R_train`: (`str`) Matrix of fan-speed vectors in training set of `N_fans` rows by `N_train` cols, matching `V_train`.
	- `R_test`: (`str`) Matrix of fan-speed vectors in test set of `N_fans` rows by `N_test` cols, matching `V_test`.
	- `N_train`: (`str`) Number of samples in the training dataset.
	- `N_test`: (`str`) Number of samples in the test dataset.
	- `N_fans`: (`str`) Number of effective actuators. Size of r-vector. Here it means number of fan-array rows since rows are coupled.
	- `N_sensors`: (`str`) Number of sensors in velocity profile. Size of v-vector.
	- `yLs`: (`str`) Spanwise coordinates of each sensor, normalized by fan-array width L. y=0 is the centerline of the fan-array.
	- `yLs_edges`: (`str`) Spanwise coordinates of only sensors aligned with edges of a fan.
	- `yLs_hubs`: (`str`) Spanwise coordinates of only sensors aligned with centers of a fan.
	- `L`: (`str`) Width of the fan-array in meters.
	- `d`: (`str`) Width of a single fan in meters.
	- `V_max`: (`str`) Nominal max. velocity of the fan-array in m/s.
	- `data`: (`str`) dict mapping x/L (`str`) → data for that location. `R_train` & `R_test` are in `"common"`. Key `"1"` has inverse design data.
	- `V_train`: (`str`) Matrix of training velocities of `N_sensors` rows by `N_train` columns. Velocities are divided by `V_max`.
	- `V_train_std`: (`str`) Matrix of corresp. standard deviations for each entry in `V_train`. Velocities are divided by `V_max`.
	- `V_test`: (`str`) Matrix of test-set velocities of `N_sensors` rows by `N_test` columns. Velocities are divided by `V_max`.
	- `V_test_std`: (`str`) Matrix of corresp. standard deviations for each entry in `V_test`. Velocities are divided by `V_max`.
	- `A`: (`str`) Surrogate model matrix for a given x/L location, of `N_sensors` rows by `N_fans` columns.
	- `b`: (`str`) Surrogate model bias vector for a given x/L location, of shape `(N_sensors,1)`.
	- `xL`: (`str`) x/L location of that dataset (where V's where measured) as a `float`.
	- `N_iv`: (`str`) Number of samples in inverse-design dataset.
	- `V_target_iv`: (`str`) Matrix of target velocities (divided by `V_max`) for inverse design, of `N_sensors` rows and `N_iv` columns.
	- `R_iv`: (`str`) Matrix of fan-speed profiles produced by inverse design to get the profiles in `V_target_iv`; `N_fans` by `N_iv`.
	- `V_pred_iv`: (`str`) Matrix of predicted velocity profiles (divided by `V_max`) according to surrogate model for `R_iv`.
	- `V_measured_iv`: (`str`) Matrix of measured velocity profiles (divided by `V_max`) when the profiles in `R_iv` were executed in lab.
	- `V_measured_iv_std`: (`str`) Matrix of standard deviations (divided by `V_max`) for each time-averaged measurement in `V_measured_iv`.
	- `1`: (`str`) Data for streamwise location x/L=1
	- `1/2`: (`str`) Data for streamwise location x/L=1/2
	- `1/4`: (`str`) Data for streamwise location x/L=1/4
	- `1/8`: (`str`) Data for streamwise location x/L=1/8
- `data`: (`dict`) dict mapping x/L (`str`) → data for that location. `R_train` & `R_test` are in `"common"`. Key `"1"` has inverse design data.
	- `1`: (`dict`) Data for streamwise location x/L=1
		- `xL`: (`float`) x/L location of that dataset (where V's where measured) as a `float`.
		- `V_train`: (`ndarray`) Matrix of training velocities of `N_sensors` rows by `N_train` columns. Velocities are divided by `V_max`.
		- `V_train_std`: (`ndarray`) Matrix of corresp. standard deviations for each entry in `V_train`. Velocities are divided by `V_max`.
		- `V_test`: (`ndarray`) Matrix of test-set velocities of `N_sensors` rows by `N_test` columns. Velocities are divided by `V_max`.
		- `V_test_std`: (`ndarray`) Matrix of corresp. standard deviations for each entry in `V_test`. Velocities are divided by `V_max`.
		- `A`: (`ndarray`) Surrogate model matrix for a given x/L location, of `N_sensors` rows by `N_fans` columns.
		- `b`: (`ndarray`) Surrogate model bias vector for a given x/L location, of shape `(N_sensors,1)`.
		- `N_iv`: (`int`) Number of samples in inverse-design dataset.
		- `V_target_iv`: (`ndarray`) Matrix of target velocities (divided by `V_max`) for inverse design, of `N_sensors` rows and `N_iv` columns.
		- `R_iv`: (`ndarray`) Matrix of fan-speed profiles produced by inverse design to get the profiles in `V_target_iv`; `N_fans` by `N_iv`.
		- `V_pred_iv`: (`ndarray`) Matrix of predicted velocity profiles (divided by `V_max`) according to surrogate model for `R_iv`.
		- `V_measured_iv`: (`ndarray`) Matrix of measured velocity profiles (divided by `V_max`) when the profiles in `R_iv` were executed in lab.
		- `V_measured_iv_std`: (`ndarray`) Matrix of standard deviations (divided by `V_max`) for each time-averaged measurement in `V_measured_iv`.
	- `1/2`: (`dict`) Data for streamwise location x/L=1/2
		- `xL`: (`float`) x/L location of that dataset (where V's where measured) as a `float`.
		- `V_train`: (`ndarray`) Matrix of training velocities of `N_sensors` rows by `N_train` columns. Velocities are divided by `V_max`.
		- `V_train_std`: (`ndarray`) Matrix of corresp. standard deviations for each entry in `V_train`. Velocities are divided by `V_max`.
		- `V_test`: (`ndarray`) Matrix of test-set velocities of `N_sensors` rows by `N_test` columns. Velocities are divided by `V_max`.
		- `V_test_std`: (`ndarray`) Matrix of corresp. standard deviations for each entry in `V_test`. Velocities are divided by `V_max`.
		- `A`: (`ndarray`) Surrogate model matrix for a given x/L location, of `N_sensors` rows by `N_fans` columns.
		- `b`: (`ndarray`) Surrogate model bias vector for a given x/L location, of shape `(N_sensors,1)`.
	- `1/4`: (`dict`) Data for streamwise location x/L=1/4
		- `xL`: (`float`) x/L location of that dataset (where V's where measured) as a `float`.
		- `V_train`: (`ndarray`) Matrix of training velocities of `N_sensors` rows by `N_train` columns. Velocities are divided by `V_max`.
		- `V_train_std`: (`ndarray`) Matrix of corresp. standard deviations for each entry in `V_train`. Velocities are divided by `V_max`.
		- `V_test`: (`ndarray`) Matrix of test-set velocities of `N_sensors` rows by `N_test` columns. Velocities are divided by `V_max`.
		- `V_test_std`: (`ndarray`) Matrix of corresp. standard deviations for each entry in `V_test`. Velocities are divided by `V_max`.
		- `A`: (`ndarray`) Surrogate model matrix for a given x/L location, of `N_sensors` rows by `N_fans` columns.
		- `b`: (`ndarray`) Surrogate model bias vector for a given x/L location, of shape `(N_sensors,1)`.
	- `1/8`: (`dict`) Data for streamwise location x/L=1/8
		- `xL`: (`float`) x/L location of that dataset (where V's where measured) as a `float`.
		- `V_train`: (`ndarray`) Matrix of training velocities of `N_sensors` rows by `N_train` columns. Velocities are divided by `V_max`.
		- `V_train_std`: (`ndarray`) Matrix of corresp. standard deviations for each entry in `V_train`. Velocities are divided by `V_max`.
		- `V_test`: (`ndarray`) Matrix of test-set velocities of `N_sensors` rows by `N_test` columns. Velocities are divided by `V_max`.
		- `V_test_std`: (`ndarray`) Matrix of corresp. standard deviations for each entry in `V_test`. Velocities are divided by `V_max`.
		- `A`: (`ndarray`) Surrogate model matrix for a given x/L location, of `N_sensors` rows by `N_fans` columns.
		- `b`: (`ndarray`) Surrogate model bias vector for a given x/L location, of shape `(N_sensors,1)`.
- `common`: (`dict`) dict containing data and parameters shared across all datasets.
	- `xLs_str`: (`tuple`) tuple of x/L values (as `str`) used as keys in `data`
	- `R_train`: (`ndarray`) Matrix of fan-speed vectors in training set of `N_fans` rows by `N_train` cols, matching `V_train`.
	- `R_test`: (`ndarray`) Matrix of fan-speed vectors in test set of `N_fans` rows by `N_test` cols, matching `V_test`.
	- `N_train`: (`int`) Number of samples in the training dataset.
	- `N_test`: (`int`) Number of samples in the test dataset.
	- `N_fans`: (`int`) Number of effective actuators. Size of r-vector. Here it means number of fan-array rows since rows are coupled.
	- `N_sensors`: (`int`) Number of sensors in velocity profile. Size of v-vector.
	- `L`: (`float`) Width of the fan-array in meters.
	- `d`: (`float`) Width of a single fan in meters.
	- `V_max`: (`int`) Nominal max. velocity of the fan-array in m/s.
	- `yLs`: (`list`) Spanwise coordinates of each sensor, normalized by fan-array width L. y=0 is the centerline of the fan-array.
	- `yLs_edges`: (`list`) Spanwise coordinates of only sensors aligned with edges of a fan.
	- `yLs_hubs`: (`list`) Spanwise coordinates of only sensors aligned with centers of a fan.

