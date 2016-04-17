### Introduction ###

Editor does simple checks when saving a track.

It shows warnings or errors in the Warnings tab (use alt-J to show).

It also provides some info with values that were checked.

Usually some short info is shown on what to change to fix them.

<br>
Errors are in red, warnings in orange, info in yellow, note in green, and just text in blue.<br>
<br>
Keep in mind that those are quite simple checks, must be fast to not delay saving.<br>
<br>
And not always a warning means that there is something wrong with/on track.<br>
<br>
Also most great looking tracks will have a warning about too many grasses or vegetation etc.<br>
<br>
<br>
This list here is a reference with all warnings and has some more info on how to fix them.<br>
<br>
It also has developer remarks when needing improvement (TODO).<br>
<br>
<i>For reference code see in <a href='https://github.com/stuntrally/stuntrally/blob/master/source/editor/Warnings.cpp'>source/editor/Warnings.cpp</a></i>

<h3>List</h3>

<h4>Start position</h4>
<table><thead><th> Error </th><th> Car start outside track area </th></thead><tbody>
<tr><td> Error </td><td> Car start below terrain      </td></tr>
<tr><td>       </td><td>                              </td></tr>
<tr><td> Info  </td><td> Car start far above terrain\n (skip this if on bridge or in pipe), distance </td></tr>
<tr><td>       </td><td> other start places inside terrain (split screen) </td></tr>
<tr><td>       </td><td>                              </td></tr>
<tr><td> Warning </td><td> Road dir check wrong, road dir is likely opposite </td></tr>
<tr><td>       </td><td> TODO: throw out dir, use this check for value </td></tr>
<tr><td> Warning </td><td> Car start isn't facing first checkpoint <br> (wrong direction or first checkpoint), distance </td></tr></tbody></table>

<h4>Checkpoints</h4>
<table><thead><th> Error </th><th> First checkpoint not set  (use ctrl-0) </th><th> </th></thead><tbody>
<tr><td> Warning </td><td> Too small checkpoint at road point     </td><td> </td></tr>
<tr><td>       </td><td>                                        </td><td> </td></tr>
<tr><td> Error </td><td> No checkpoints set (use K,L on some road points) </td><td> </td></tr>
<tr><td> Info  </td><td> Too few checkpoints (add more), count  </td><td> numChks < 3 </td></tr></tbody></table>

<h4>Road</h4>
<table><thead><th> Info </th><th> HQ Road </th><th> mtr >= 3 </th></thead><tbody>
<tr><td> Info </td><td> Too few road materials used </td><td> <= 1     </td></tr>
<tr><td>      </td><td>         </td><td>          </td></tr>
<tr><td> Warning </td><td> Car start width small </td><td> width < 8 or width < rdW <b>1.4</b></td></tr>
<tr><td> Warning </td><td> Car start height small </td><td> height < 4.5 </td></tr>
<tr><td>      </td><td>         </td><td>          </td></tr>
<tr><td> Warning </td><td> Extremely low checkpoints ratio, add more </td><td>          </td></tr>
<tr><td> Warning </td><td> Very few checkpoints ratio, add more </td><td>          </td></tr>
<tr><td>      </td><td>         </td><td>          </td></tr>
<tr><td> Warning </td><td> Road points (on average) are very far <br>(corners could behave sharp and straights become not straight) </td><td> len > 85 </td></tr>
<tr><td> Info </td><td> Road points are far </td><td> > 60     </td></tr></tbody></table>

<table><thead><th> Road has over 200 points, use recommended merge length 600 or more </th></thead><tbody>
<tr><td> Road has over 120 points, use recommended merge length 300 or more </td></tr>
<tr><td> Road has over 50 points, use recommended merge length 80 or more   </td></tr>
<tr><td> TODO: make this auto, and only some bias 0..2 param                </td></tr></tbody></table>

<h4>Terrain</h4>
<table><thead><th> Error </th><th> Using too big heightmap 2048, file size is 16MB </th><th> </th></thead><tbody>
<tr><td> Info  </td><td> Using big heightmap 1024, file size is 4MB      </td><td> </td></tr>
<tr><td> Info  </td><td> Using too small heightmap                       </td><td> 128 </td></tr>
<tr><td>       </td><td>                                                 </td></tr>
<tr><td> Info  </td><td> Terrain triangle size is small                  </td><td> < 0.9 </td></tr>
<tr><td> Info  </td><td> Terrain triangle size is big                    </td><td> > 1.9 </td></tr>
<tr><td>       </td><td>                                                 </td></tr>
<tr><td> Info  </td><td> HQ Terrain                                      </td><td> layers = 4 </td></tr>
<tr><td> Error </td><td> Too many terrain layers used, max 4 possible    </td><td> > 4 </td></tr>
<tr><td> Info  </td><td> Too few terrain layers used                     </td><td> <= 2 </td></tr></tbody></table>

<h4>Vegetation</h4>
<table><thead><th> Info </th><th> HQ Vegetation </th><th> models >= 5 </th></thead><tbody>
<tr><td> Warning </td><td> Too many models used, not recommended </td><td> veg >= 7    </td></tr>
<tr><td> Info </td><td> Too few models used </td><td> veg <= 2    </td></tr>
<tr><td>      </td><td>               </td><td>             </td></tr>
<tr><td> Error </td><td> Vegetation use is huge, trees density is </td><td> > 3.1       </td></tr>
<tr><td> Warning </td><td> Using a lot of vegetation, trees density is </td><td> > 2         </td></tr>
<tr><td>      </td><td>               </td><td>             </td></tr>
<tr><td> Warning </td><td> Smooth grass density is high saving will take long time" </td><td> > 10        </td></tr></tbody></table>

<h4>Grass</h4>
<table><thead><th> Info </th><th> HQ Grass </th><th> layers >= 4 </th></thead><tbody>
<tr><td> Warning </td><td> Too many grasses used, not recommended </td><td> >= 5        </td></tr>
<tr><td> Info </td><td> Too few grasses used </td><td> <= 2        </td></tr></tbody></table>

<h4>Total Quality</h4>
<table><thead><th> </th><th> hq = hqTerrain + hqGrass + hqVeget + hqRoad </th></thead><tbody>
<tr><td> Info </td><td> Quality too high (possibly low Fps), try to reduce densities or layers/models/grasses count </td><td> hq > 3                                      </td></tr>
<tr><td> Info </td><td> Great quality, but don't forget about some optimisations </td><td> hq > 2                                      </td></tr>
<tr><td> Info </td><td> Low quality (ignore for deserts), try to add some layers/models/grasses </td><td> hq = 0                                      </td></tr></tbody></table>

<h3>Other</h3>

Things that are not checked but should be, TODO:<br>
<ul><li>Gui button for a complex (long time) check<br>
</li><li>terrain error vs(and) complexity<br>
</li><li>highest slopes (triplanar) used more than twice, used on low angle layers (not needed)<br>
</li><li>blendmap layers coverage (used area %), % of blending between (separation), default layer % (no range), noise ..<br>
</li><li>grass dens map % mul by trk grass dens</li></ul>

<ul><li>! use of vegetation models, real counts. 1 model used few times isn't that bad as many models used constantly..<br>
</li><li>static objects count, different (and mtr? pers use 1), (we need hw_inst)<br>
</li><li>paged-geom:? page size small, distance big, try hw_inst..