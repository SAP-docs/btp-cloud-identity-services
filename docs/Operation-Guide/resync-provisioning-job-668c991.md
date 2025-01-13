<!-- loio668c99120f244df19fd63b8788409b48 -->

# Resync Provisioning Job

The *Resync* job reads all entities from the source system and provisions all entities to the target system.

This job performs a full replace of entities in the target system with entities from the source system. You can use it to fix inconsistent data between both systems. For example, when an entity has been changed or deleted in the target system only.

A Resync job overwrites changes in the target system. As a result, the data between the source and the target system becomes consistent again.

To run a resync job, select a source system and choose *Jobs* \> *Resync Job* \> *Run Now*. This starts a resync job immediately.

> ### Note:  
> Normally, you don’t schedule a *Resync Job* as it is expected to be run on demand.

