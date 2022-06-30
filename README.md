# autotest-docker
A repository for the docker files required to test the nbgrader:autotest branch.

# Demo
To run the demo, make sure Docker is installed on your machine, and run the following
in the root folder of the repository:
```
docker-compose up
```
This will build a docker image, bind mount the `demo/source` and `release` folders,
and start a Jupyter notebook server. Open your browser and navigate to `localhost:8888`; 
this should open the Jupyter notebook interface.

You will likely need to give read/write permissions to the `source`, `release`, and `instantiated` folders
(so that the `jupyter` user inside the docker container can read/write to them).
Again in the root folder of the repository, run:
```
chmod a+rwx source
chmod a+rwx release
chmod a+rwx instantiated
```

We have included a few example autograded notebooks in this demo container.
For example, you can use Autotest to process the `ps3` assignment.
In the Jupyter notebook interface in your browser, open a terminal (`New -> Terminal`)
and type:
```
nbgrader generate_assignment --force ps3
or
nbgrader instantiate_tests --force ps3

```
To see how Autotest processes your questions, you can instead run with debug flags:
```
nbgrader generate_assignment --force --debug ps3
or 
nbgrader instantiate_tests --force --debug ps3
```
The release version of the assignment will appear with generated test code in the `release/` folder.
The instantiated version of the assignment including the solutions will appear with generated test code in the `instantiated/` folder.

See the `source/` folder for other demo assignments. You can also add your own in the `source/` folder 
of this repository. Make sure to give `a+rwx` permissions to each assignment you add to the folder, 
as otherwise the jupyter user won't be able to read/write to them.
