.. _cli:

Command Line Interface
=======================

.. currentmodule:: rastervision

The Raster Vision command line utility, ``rastervision``, is installed with a ``pip install`` of
``rastervision``, which is installed by default in the :ref:`docker containers`.
It has subcommands, with some top level options:

.. command-output:: rastervision --help

Commands
--------

.. _run cli command:

run
^^^

Run is the main interface into running ``ExperimentSet`` workflows.

.. command-output:: rastervision run --help

Some specific parameters to call out:

-\\-arg
~~~~~~~~~~~

Use ``-a`` to pass arguments into the experiment methods; many of which take a ``root_uri`` which is where Raster Vision will store all the output of the experiment. If you forget to supply an argument, Raster Vision will remind you.

-\\-dry-run
~~~~~~~~~~~

Using the ``-n`` or ``--dry-run`` flag is useful to see what you're about to run before you run it. Combine this with the verbose flag for different levels of output:

.. code:: shell

   > rastervision run spacenet.chip_classification -a root_uri s3://example/ --dry_run
   > rastervision -v run spacenet.chip_classification -a root_uri s3://example/ --dry_run
   > rastervision -vv run spacenet.chip_classification -a root_uri s3://example/ --dry_run

-\\-skip-file-check
~~~~~~~~~~~~~~~~~~~

Use ``--skip-file-check`` or ``-x`` to avoid checking if files exist, which can take a long time for large experiments. This is useful to do the first run, but if you haven't changed anything about the experiment and are sure the files are there, it's often nice to skip that step.

.. _run split option:

-\\-splits
~~~~~~~~~~

Use ``-s N`` or ``--splits N``, where ``N`` is the number of splits to create, to parallelize commands that can be split into parallelizable chunks. See :ref:`parallelizing commands` for more information.

.. _predict cli command:

predict
^^^^^^^

Use ``predict`` to make predictions on new imagery given a :ref:`predict package`.

.. command-output:: rastervision predict --help

ls
^^^

The ``ls`` command very simply lists the IDs of experiments in the given module or file.
This functionality is likely to expand to give more information about expriments discovered
in a project in later versions.

.. command-output:: rastervision ls --help

run_command
^^^^^^^^^^^

The ``run_command`` is used to run a specific command from a serialized command configuration.
This is likely only useful to people writing :ref:`experiment runner` that want to run
commands remotely from serialzed command JSON.

.. command-output:: rastervision run_command --help
