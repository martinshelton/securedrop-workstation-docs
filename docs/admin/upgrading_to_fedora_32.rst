Upgrading to Fedora 32
======================

.. include:: ../includes/top-warning.rst

.. note:: This advisory was written in November 2020, and will be removed when a new
          version of Qubes that contains the Fedora 32 template is released.

Why do I need to upgrade?
-------------------------

SecureDrop Workstation makes use of several Fedora-based VMs which are part of
a Qubes installation by default, including ``sys-firewall``, ``sys-net``, ``sys-
usb``, ``work``, and ``vault`` . In Qubes 4.0.3, these VMs are based on a
Fedora 30 template.

As of May 26, 2020, Fedora 30 templates are end-of-life. If you are
provisioning SecureDrop Workstation for the first time, you will need to update
your Fedora template manually to Fedora 32 *before* installing SecureDrop
Workstation.

If you are an existing SecureDrop Workstation user, SecureDrop Workstation
will install the template automatically when updates are applied, but you
should also :ref:`manually configure <configure_vms>` VMs not managed by
SecureDrop Workstation to use the Fedora 32 template.

Install Fedora-32 template
--------------------------

In a ``dom0`` terminal (**Qubes Application Menu > Terminal Emulator**), type
the following to download the Fedora 32 template:

.. code:: sh

   sudo qubes-dom0-update qubes-template-fedora-32

You will see some information from the package manager, including a progress
bar.

When the download has concluded, you will be prompted to install the package.
Type ``y`` to proceed with the installation.


Update the Fedora-32 template
-----------------------------
Once the template installation is complete, update the template using the Qubes
Updater. Click **Q > System Tools > Qubes Update** in the application menu.
Click the checkbox "Enable updates for qubes without known updates" option,
and click the checkbox next to ``fedora-32``. Click **Next** and wait for
any available updates to be downloaded and applied.

.. _configure_vms:

Configure VMs to use the new template
-------------------------------------
To apply the template to VMs that currently use an older version, open the
Qube Manager via **Q > System Tools > Qube Manager**. All VMs will be visible at
a glance; to change a VM's settings, right-click it and select **Qube Settings**.

In the Qube Settings window, select ``fedora-32`` from the drop-down menu
beside **Template**, then click **OK.**

|screenshot_qsettings_fedora32|

You should perform this process for:

  - ``work``
  - ``vault``
  - ``sys-net``
  - ``sys-usb``
  - ``sys-firewall``.

Existing SecureDrop Workstation users may perform this process for ``work`` and
``vault`` only, as the other VMs will be updated by SecureDrop Workstation.

Reboot the system to ensure the changes take effect. Alternatively, you can
restart only the VMs you have updated. If you get a ``sys-whonix`` prompt asking how you want to connect to the Tor network, select the "Connect" option, which allows a direct connection to the Tor network.

.. tip::

   You can also use the **Qubes Template Manager** (also in **Q > System Tools**)
   to make template changes. However, note that it will not allow you to make
   template changes for VMs that are currently running, so you may have to
   manually shut down VMs in the correct order to do so.

.. |screenshot_qsettings_fedora32| image:: ../images/screenshot_qsettings_fedora32.png

Getting Support
---------------

.. include:: ../includes/getting_support.rst
