# NRPS/PKS modules

*Added in antiSMASH 5.1*

NRPS and PKS products come from assembly lines of modules.
These modules are detected by antiSMASH and will be shown in the `NRPS/PKS domains` tab for a region, along with the domains from previous versions.

Here is an example of a single gene with multiple modules:

![multimodule](../img/modules_multiple.png)

These modules shown are *complete*, in that they have a loader domain (e.g. adenylation or acyltransferase) and a carrier protein (e.g. `ACP`).
Complete modules may also have a starter domain (e.g. condensation or ketosynthase).
In the case of a trans-AT-PKS module, provided it has a trans-AT specific ketosynthase,
it will have no loader domain within the module, and the loaded substrate will be assumed to be Malonyl-CoA.

At the top of the section is a button `Show module domains` that will hide the module graphic and show the domains similarly to previous versions of antiSMASH.
The module borders and backgrounds will still be shown to indicate the extents of the module.
The same example from above is shown below with this domain option enabled.

![multimodule-domains](../img/modules_multiple_domains.png)

The thioesterase (`TE`) domain shown is included in the final module.
It is not hidden by the module graphic due to being important for a whole product.

Moving the mouse cursor over a *complete* module will hide the module graphic and display the component domains.
These domains can be clicked on to access specific information (this behaviour has not changed with the addition of modules).

#### Modifications

The second module in the above examples has a modification domain (`nMT` or N-methyltransferase).
Modification domains contained by a module will modify the loaded substrate, with the modified substrate (or *monomer*), being displayed on the module.
In the examples above, the adenylation domain (`A`) is predicted to load leucine (`leu`), and is then modified by the module to be a N-methylated leucine (`NMe-leu`).

#### Incomplete modules and incomplete predictions

![module-types](../img/modules_types.png)

Not all modules will be considered *complete* like `orf_R7` in the image above.
It is common to have large fragments of domains and multiple domains that by themselves don't complete a module.
In cases where these domains are found and cannot form a *complete* module, an *incomplete* module will be formed.
Incomplete modules are shown with a dashed outline and will always show component domains, an example is `orf_R6` in the image above.
In the case of a loader domain without a carrier protein, the predicted substrate that would be loaded is not considered for a candidate cluster's polymer prediction.

There are also occasions, even in a complete module, where no consensus can be found for the prediction of a loaded substrate.
In these cases, the module will still be shown, but the substrate will be shown as `?` as shown for `orf_R8` in the image above.
Complete modules with unknown substrates will still apply modifications, thus monomers like `D-NMe-?` are possible.
For the purposes of a candidate cluster's polymer, these unknown predictions will use the generic `nrp`/`X` SMILES strings.


#### Iterative polyketides

In the case of a `PKS_KS` domain being iterative, the module will show an additional icon. For example:

![iterative](../img/modules_iterative.png)

The number of iterations is not determined, and only a single monomer (in this case `mal`) will be added to the candidate cluster's final polymer.
