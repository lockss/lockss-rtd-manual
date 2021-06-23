==============================
Using the Kubernetes Dashboard
==============================

Kubernetes comes with the `Kubernetes Dashboard <https://kubernetes.io/docs/tasks/access-application-cluster/web-ui-dashboard/>`_, a web-based user interface (UI).

To facilitate installing and interacting with the Kubernetes Dashboard, the LOCKSS Installer offers the :program:`dashboard-util` script.

-----------------------------------
Installing the Kubernetes Dashboard
-----------------------------------

To install the Kubernetes Dashboard, run this command [#fn1]_:

.. code-block:: shell

   scripts/dashboard-util --install

----------------------------------
Accessing the Kubernetes Dashboard
----------------------------------

To access the Kubernetes Dashboard:

1. Create a secure channel to your K3s cluster with the following command:

   .. code-block:: shell

      k3s kubectl proxy &

   .. note::

      This command runs in the background "forever".

2. Obtain the login URL with the following command:

   .. code-block:: shell

      scripts/dashboard-util --url

3. Obtain the login token with the following command:

   .. code-block:: shell

      scripts/dashboard-util --token

4. Open a browser and go to the login URL.

5. Make sure the :guilabel:`Token` radio button is selected.

6. Copy and paste the login token into the :guilabel:`Enter token` text field.

---------------------------------
Using the Kubernetes Dashboard UI
---------------------------------

When the dashboard comes up, it will be in the default namespace. Click on the namespace pull-down menu near the top and select the ``lockss`` namespace to see the LOCKSS components. If all of your deployments are running and ready, the three circles at the top should be green. In the left hand panel you can select the components you are interested in:

*  Click on :guilabel:`Services` to see the cluster IP for each of the running services. You can click on a specific service to see more detailed information.

*  Click on :guilabel:`Deployments` to see a list of services and their CPU and memory usage. You can access specific services and deployments from here.

*  Click on :guilabel:`Pods`. This will give you information about all the pods running. Click on a pod of interest to obtain more granular information:

   :guilabel:`View logs`
      Since LOCKSS output logs are persisted to a local directory, there will be very little in the Kubernetes logs if the container came up without errors.

   :guilabel:`Exec into pods`
      This will open a terminal window into the container.

   :guilabel:`Edit the pod resource`
      This will allow you to view and edit the YAML file which was used to start the pod. The edit will not persist on restart.

   :guilabel:`Delete the pod`
      While this will delete the current pod, a new pod will be spawned by the deployment with a new pod ID.

---------------------------------
Updating the Kubernetes Dashboard
---------------------------------

To update the Kubernetes Dashboard to the most recent release, run this command [#fn1]_:

.. code-block:: shell

   scripts/dashboard-util --update

---------------------------------
Removing the Kubernetes Dashboard
---------------------------------

To remove the Kubernetes Dashboard from the ``kubernetes-dashboard`` namespace, run this command [#fn1]_:

.. code-block:: shell

   scripts/dashboard-util --remove

----

.. rubric:: See Also

*  `Web UI (Dashboard) <https://kubernetes.io/docs/tasks/access-application-cluster/web-ui-dashboard/>`_ on the Kubernetes website.

----

.. rubric:: Footnotes

.. [#fn1]

   This command is relative to the ``lockss`` user's :file:`lockss-installer` directory.
