---
description: Common misconceptions with TF2 that mastercomfig corrects.
...

# Misconceptions

## Opciones de lanzamiento malas

* **-noipx** : No existe y nunca existió en Source.
* **-heapsize** : No existe. Realmente nunca funcionó en Source y fue removido en una [antigua actualización](https://store.steampowered.com/oldnews/4371)
* **-nocrashdialog** : No mejora FPS, ademas crea errores dificiles de depurar.
* **+exec autoexec** : `autoexec.cfg` ya se está ejecutando al iniciar, no es necesario ejecutarlo nuevamente.
* **+map_background** : Team Fortress 2 has a much more advanced preload system now, so map backgrounds are not needed. If you are using them to bypass sv_pure through preloading, that's fine
* **-dxlevel 98** : Esto solamente es soportado en Xbox 360. Will fallback to `-dxlevel 95` on PC
* **-dxlevel 82** : this was an old DXLevel only used by certain ancient-by-today's-standards NVIDIA cards. It does not do anything anymore
* **-limitvsconst** : limits the hardware vertex shader constants to 256, possibly below hardware capabilities, which does save a bit of resources. But, with more constants available, faster shader modes can be used
* **-threads** : the Source Engine automatically determines the value for this, and caps it at 3, due to performance issues with higher values. Valve also [recommends](https://www.reddit.com/r/GlobalOffensive/comments/5y8r7v/in_depth_discussion_of_the_threads_launch_option/dep5yno/) removing this launch option
* **-high** : `high` is a priority mode in Windows that is only recommended for short-lived, time critical threads. It can unbalance resource usage and decrease performance. Close applications on your PC instead
* **-nod3d9ex** : this disables extensions which improve resource management, speed up alt-tabs and improve memory usage. Ages ago, drivers did not support this option very well, and people recommended disabling it, but now, it is all good and there is no reason to use this launch option
* **-NOPROCESSHEAP** : this was a workaround for a bug that only happened for a short time in CS:GO, and it decreases performance. There is absolutely no reason to use this anymore

## Resoluciones y ventanas en las opciones de lanzamiento

* **-fullscreen -w -h -full -sw -window -windowed -width -height**

Estas opciones de lanzamiento puede generar un modo de video impropio, cosa que es no de preferencia por el material system y puede reducir el rendimiento. Intenta estas opciones en la ventana de ajustes.

## Malos CVars

* `mat_shadowstate` : No existe.
* `mat_parallaxmap` : No se usa.
* `g_ragdoll_fadespeed 0;g_ragdoll_lvfadespeed 0` : No se usa. If it did work, setting it to 0 would make ragdolls never fade.
* `mp_usehwmvcds` : Not used.
* `cl_rumblescale 0` : `-nojoy` already disables this, and setting it to 0 has little to no benefit.
* `r_threaded_client_shadow_manager` : Not used.
* `r_threaded_renderables` : Not used.
* `in_usekeyboardsampletime ` : Not used unless you use keylook, and you probably would not want this off if you did.
* `mat_wateroverlaysize` : Not used, debug only command.
* `mat_framebuffercopyoverlaysize` : Not used, debug only command.
* `r_decal_cullsize` : Not used.
* `rate 60000` : This is lower than the TF2 default rate of `80000`. TF2 default network settings are already on the low-end. Why would you set rate lower, especially when you're increasing packet rates? (`cl_updaterate 66`, `cl_cmdrate 66`)?
* `cl_interp 0.033` : This is a typo that was made somewhere along the way. The correct interp is `cl_interp_ratio 2;cl_interp 0.0303`. This is equal to 2 / 66.
* `cl_interp 0.0152` : This means you will be subject to inaccurate extrapolation which is not in line with the server's history, all for getting lower visual latency on entity positions within a few milliseconds, which doesn't matter when positions cannot be substantially different within that time. Instead, you will want to make sure your entity positions are at least in line with the server's history as that is substantially more important for lag compensation and your own perception when predicting position based on velocity/trajectory.
* `mat_max_worldmesh_vertices 512` : The minimum value for this is 1024, not 512. This also increases the number of meshes used for the world, while reducing mesh complexity. This trade-off is only worth it for very, very bad GPUs, like integrated graphics cards with no or poor hardware accelerated transform and vertex shader support.
* `mat_forcehardwaresync 0` : This makes the engine produce frames out of sync from the GPU processing, increasing input lag.
* `mem_max_heapsize 2048` : No need to adjust the cap for the heap to be wildly large, and the memory system initializes before this variable can apply anyway. If it did work, Source already determines the best value from your memory size and caps it using this console variable. Setting it high will [take away memory](https://github.com/ValveSoftware/Source-1-Games/issues/1543#issuecomment-520534294) from other things, and also increase pause times for memory management.
* `datacachesize 512` : No need to adjust this to be wildly large, Source can decide the best value and if you increase it for no reason, you'll reduce the amount of heap available for other things other than the datacache.
* `sv_forcepreload`/`cl_forcepreload` : [cl_forcepreload was removed](https://www.teamfortress.com/post.php?id=19733) - "Fixed two most common forms of framerate stuttering / hitching when using popular FPS configs". It has also been called [cl_massive_hitches_at_surprising_times 1](https://www.reddit.com/r/GlobalOffensive/comments/adq2a4/never_install_csgo_on_an_old_hard_drive/edlbh3d/) by a Valve employee.
* `rope_averagelight 0` : Setting this to 0 loops through cubemaps to set ropes to use maximum intensity rather than the already available average intensity, so it reduces performance.
* `r_PhysPropStaticLighting 0` : This disables caching static lighting on props.
* `r_lod 2` : This forces everything to LOD 2, when the lowest quality is LOD 7. Set this to `r_lod -1` and let `r_rootlod` handle base quality while still allowing for lower qualities to be used at a distance.