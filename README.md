# Cantera Example Data Files

This repository provides data files used by various Cantera examples, which can be seen
at https://cantera.org/stable/examples/python/index.html. In particular, many of the
input files found here are based on scientific publications and are meant to demonstrate
Cantera's capabilities with more realistic and interesting reaction systems than those
based only on the basic mechanisms provided in the main Cantera repository.

> [!IMPORTANT]
> **Licensing and Attribution Notice**
>
> The Cantera project is not the original author of the reaction mechanisms included
> in this repository and is not claiming to grant a license to them. The mechanisms
> were assembled by their respective researchers and appear to be shared without
> restrictive licensing requirements.
>
> **If you use this data in scientific publications, please cite the original papers**
> associated with each mechanism. Suitable citations are included in the `description`
> field of each mechanism file.

## Adding files for new examples

To implement an example requiring a new input file, the following steps should be
followed:

- Create your new example in your local Git checkout of Cantera.
- Create the new input file in the `data/example_data` subdirectory.
- Commit the example to a new feature branch.
  * :warning: Make sure you _do not_ add the input file or an update of the
    `example_data` submodule to this branch.
- Commit the input file to a feature branch in the `example_data` submodule.
- Create a pull request for your example in the main Cantera repository
- Create a pull request in the `cantera-example-data` repository which includes the text
  `(Cantera/cantera#XYZ)` where `XYZ` is the number of your PR in the main repository.
  * The CI process in the main repository will automatically check out this submodule
    PR so the new input file is available for those jobs that run the examples.
  * You should see one failing job, with the description `Linters / Check for unmerged
    example-data pull request (pull_request)`. This is a reminder for maintainers for
    the remaining steps that need to be completed before merging the PR.
- Once PR reviews are completed and all expected tests pass, the PR on the
  `cantera-example-data` can be merged.
- Finally, the PR branch for the main repository can be updated to include the update
  of the `example_data` submodule, and this PR can be merged.
