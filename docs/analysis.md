
We provide some visualization videos and qualitatively analysis on Bench2Drive that compare our approach **ORION** to baseline.For TCP, UniAD and VAD, we choose the best version of these models(TCP-traj,UniAD-Base,VAD-Base), and make visualization on 10 Scenarios as below. 

**Note: It might take some time to load all gifs. Please be patient.**

<table>
  <tr>
    <th rowspan="2" style="text-align:center">  Driving Skill </th> <th rowspan="2" style="text-align:center"> Scenario Name </th> <th rowspan="2" style="text-align:center"> Route ID </th><th colspan="5" style="text-align:center"> Success </th> 
  </tr>
  <tr>
    <td> AD-MLP </td> <td> TCP-traj </td><td>UniAD-Base</td><td>VAD-Base</td><<td><strong><font color="#add8e6">ORION</font></strong></td>
  </tr>

  <tr>
    <td rowspan="2" style="text-align:center">Merging</td>
    <td>MergerIntoSlowTraffic</td> 
    <td>2283</td> 
    <td>x</td><td>√</td><td>√</td><td>x</td><td>√</td>
  </tr>
  <tr>
    <td>SignalizedJunctionLeftTurn</td>
    <td>4183</td>
    <td>x</td><td>√</td><td>x</td><td>√</td><td>√</td>
  </tr>
  <tr>
    <td rowspan="2" style="text-align:center">Overtaking</td>
    <td>ParkedObstacle</td> 
    <td>25318</td> 
    <td>x</td><td>x</td><td>x</td><td>√</td><td>√</td>
  </tr>
  <tr>
    <td>HazardAtSideLane</td>
    <td>25439</td>
    <td>x</td><td>x</td><td>√</td><td>√</td><td>√</td>
  </tr>
  <tr>
    <td rowspan="2" style="text-align:center">Emergency Brake</td>
    <td>ParkingCutIn</td> 
    <td>18305</td> 
    <td>x</td><td>√</td><td>√</td><td>x</td><td>√</td>
  </tr>
  <tr>
    <td>StaticCutIn</td>
    <td>26396</td>
    <td>x</td><td>x</td><td>√</td><td>√</td><td>√</td>
  </tr>
  <tr>
    <td rowspan="2" style="text-align:center">Give Way</td>
    <td>YieldToEmergencyVehicle</td> 
    <td>3378</td> 
    <td>x</td><td>x</td><td>x</td><td>x</td><td>x</td>
  </tr>
  <tr>
    <td>InvadingTurn</td> 
    <td>2802</td> 
    <td>x</td><td>√</td><td>√</td><td>x</td><td>√</td>
  </tr>
  <tr>
    <td rowspan="2" style="text-align:center">Traffic Sign</td>
    <td>EnterActorFlow</td> 
    <td>3749</td> 
    <td>x</td><td>√</td><td>x</td><td>x</td><td>√</td>
  </tr>
  <tr>
    <td>VanillaNonSignalizedTurnEncounterStopsign</td>
    <td>3905</td>
    <td>x</td><td>√</td><td>x</td><td>x</td><td>√</td>
  </tr>
</table>

**Note: In this visualization, the definition of 'success' differs from the standard definition used in the Bench2Drive**. A route may involve multiple actions, such as turning after passing through a traffic light. In this visualization, we only evaluate whether the selected segment's action is successful. For example, if the vehicle obeys the traffic light and passes through the intersection, but collides while turning, it is still considered a successful case in following traffic sign.

# Merging
we visualize the behavior of three models on `MergeIntoSlowTraffic` and `SignalizedJunctionLeftTurn` scenarios to show their ability of mering . The ego vehicle should drive to off-ramp to exit the highway in `MergeIntoSlowTraffic`, and it should perform a left turn in `SignalizedJunctionLeftTurn`.

<table>
  <tr>
    <th> Case ID </th> <th> Models </th> <th> Scenario </th><th>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Front&nbsp;Camera&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;</th><th>&nbsp;&nbsp;&nbsp;&nbsp;BEV&nbsp;&nbsp;&nbsp;&nbsp;</th><th>Success</th><th>Qualitatively Analysis</th>
  </tr>
  <tr>
    <td> 1 </td> <td> TCP-traj </td> <td>MergeInto<br>SlowTraffic</td><td><img src="../assets/gifs/2283_tcp_rgb_front_MergerIntoSlowTraffic_success.gif"></td><td><img src="../assets/gifs/2283_tcp_bev_MergerIntoSlowTraffic_success.gif"></td> <td> √ </td><td> The ego vehicle carefully changes the lane and exits highway successfully, but at a quite low speed (the video is at x2 speed).</td>
  </tr>  <tr>
    <td> 2 </td><td>  UniAD-Base </td> <td>MergeInto<br>SlowTraffic</td><td><img src="../assets/gifs/2283_uniad_rgb_front_MergerIntoSlowTraffic_success.gif"></td><td><img src="../assets/gifs/2283_uniad_bev_MergerIntoSlowTraffic_success.gif"></td><td> √ </td><td> The ego vehicle makes a lane change at a high speed, exits highway successfully.</td>
  </tr>
  <tr>
    <td> 3 </td><td>  VAD-Base </td> <td>MergeInto<br>SlowTraffic</td><td><img src="../assets/gifs/2283_vad_rgb_front_MergerIntoSlowTraffic_failed.gif"></td><td><img src="../assets/gifs/2283_vad_bev_MergerIntoSlowTraffic_failed.gif"></td><td> x </td><td> The ego vehicle detects the car at front right, but still drives too fast and crashes into it.</td>
  </tr>
    <tr>
    <td> 4 </td> <td><strong><font color="#add8e6">ORION</font></strong></td> <td>MergeInto<br>SlowTraffic</td><td><img src="../assets/gifs/Orion_rgb/RouteScenario_2283_rep0_Town12_MergerIntoSlowTraffic_1_15_03_12_07_43_25.gif"></td><td><img src="../assets/gifs/Orion_bev/RouteScenario_2283_rep0_Town12_MergerIntoSlowTraffic_1_15_03_12_07_43_25.gif"></td><td> √ </td><td> ORION detects the car on the front right, slows down, and then changes the lane.</td>
  </tr>
  <tr>
    <td> 5 </td><td>  TCP-traj </td> <td>Signalized<br>Junction<br>LeftTurn</td><td><img src="../assets/gifs/4183_tcp_rgb_front_SignalizedJunctionLeftTurn_success.gif"></td><td><img src="../assets/gifs/4183_tcp_bev_SignalizedJunctionLeftTurn_success.gif"></td> <td> √ </td><td> The ego vehicle predicts appropriate trajectory and turns left at junction successfully.</td>
  </tr>  <tr>
    <td> 6 </td><td>  UniAD-Base </td> <td>Signalized<br>Junction<br>LeftTurn</td><td><img src="../assets/gifs/4183_uniad_rgb_front_SignalizedJunctionLeftTurn_failed.gif"></td><td><img src="../assets/gifs/4183_uniad_bev_SignalizedJunctionLeftTurn_failed.gif"></td><td> x </td><td> The ego vehicle fails to detect the car coming in opposite direction and continues to drive ahead, results in crash.</td>
  </tr>
  <tr>
    <td> 7 </td><td>  VAD-Base </td> <td>Signalized<br>Junction<br>LeftTurn</td><td><img src="../assets/gifs/4183_vad_rgb_front_SignalizedJunctionLeftTurn_success.gif"></td><td><img src="../assets/gifs/4183_vad_bev_SignalizedJunctionLeftTurn_success.gif"></td><td> √ </td><td> The ego vehicle detects and predicts motions of nearby vehicles, and makes left turn smoothly.</td>
  </tr>
  <tr>
    <td> 8 </td><td><strong><font color="#add8e6">ORION</font></strong></td> <td>Signalized<br>Junction<br>LeftTurn</td><td><img src="../assets/gifs/Orion_rgb/RouteScenario_4183_rep0_Town12_SignalizedJunctionLeftTurn_1_0_03_12_16_16_32.gif"></td><td><img src="../assets/gifs/Orion_bev/RouteScenario_4183_rep0_Town12_SignalizedJunctionLeftTurn_1_0_03_12_16_16_32.gif"></td><td> √ </td><td>ORION waits for the traffic light to turn green and go straight ahead, and stops when it turns red. In addition, ORION avoids collisions with opposing vehicles. After passing the traffic light, ORION also plans the trajectory to avoid the ego car deviating from the lane center line.</td>
  </tr>

</table>

# Overtaking

We visualize the behavior of three models on `ParkedObstacle` and `HazardAtSideLane` scenarios to show their ability of overtaking. The ego vehicle encounters a parked vehicle blocking part of the lane in `ParkedObstacle`, and encounters a slow-moving hazard blocking part of the lane in `HazardAtSideLane`.It should perform a lane change to avoid it.

<table>
  <tr>
    <th> Case ID </th><th> Models </th> <th> Scenario </th><th>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Front&nbsp;Camera&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;</th><th>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;BEV&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;</th><th>Success</th><th>Qualitatively Analysis</th>
  </tr>
  <tr>
    <td> 9 </td><td> TCP-traj </td> <td>ParkedObstacle</td><td><img src="../assets/gifs/25318_tcp_rgb_front_ParkedObstacle_failed.gif"></td><td><img src="../assets/gifs/25318_tcp_bev_ParkedObstacle_failed.gif"></td> <td> x </td><td> The ego vehicle tries to avoid the parked vehicle, but because of inaccurate and instabe planing, it still collides against it.</td>
  </tr>  <tr>
    <td> 10</td><td>  UniAD-Base </td> <td>ParkedObstacle</td><td><img src="../assets/gifs/25318_uniad_rgb_front_ParkedObstacle_failed.gif"></td><td><img src="../assets/gifs/25318_uniad_bev_ParkedObstacle_failed.gif"></td><td> x </td><td> The ego vehicle detects the parked car, but predicts wrong trajectory, and collides against it.</td>
  </tr>
  <tr>
    <td> 11 </td><td>  VAD-Base </td> <td>ParkedObstacle</td><td><img src="../assets/gifs/25318_vad_rgb_front_ParkedObstacle_success.gif"></td><td><img src="../assets/gifs/25318_vad_bev_ParkedObstacle_success.gif"></td><td> √ </td><td> The ego vehicle detects the parked car and turns left to avoid the car and cars coming behind.</td>
  </tr>
  <tr>
    <td> 12 </td><td><strong><font color="#add8e6">ORION</font></strong></td> <td>ParkedObstacle</td><td><img src="../assets/gifs/Orion_rgb/RouteScenario_25318_rep0_Town05_ParkedObstacle_1_20_03_12_07_43_25.gif"></td><td><img src="../assets/gifs/Orion_bev/RouteScenario_25318_rep0_Town05_ParkedObstacle_1_20_03_12_07_43_25.gif"></td><td> √ </td><td> ORION detects a stopped car, stops and waits for the time to change lanes. ORION successfully changes the lane to the left without colliding with the car from left behind.</td>
  </tr>
  <tr>
    <td> 13 </td><td>  TCP-traj </td> <td>HazardAtSideLane</td><td><img src="../assets/gifs/25439_tcp_rgb_front_HazardAtSideLane_failed.gif"></td><td><img src="../assets/gifs/25439_tcp_bev_HazardAtSideLane_failed.gif"></td> <td> x </td><td> The ego vehicle's behavior is confusing. It drives onto sidewalk and collides against cyclist.(the video is at x2 speed)</td>
  </tr>  
  <tr>
    <td> 14 </td><td>  UniAD-Base </td> <td>HazardAtSideLane</td><td><img src="../assets/gifs/25439_uniad_rgb_front_HazardAtSideLane_success.gif"></td><td><img src="../assets/gifs/25439_uniad_bev_HazardAtSideLane_success.gif"></td><td> √ </td><td> The ego vehicle detects cyclists and makes a left lane change smoothly.</td>
  </tr>
  <tr>
    <td> 15 </td><td>  VAD-Base </td> <td>HazardAtSideLane</td><td><img src="../assets/gifs/25439_vad_rgb_front_HazardAtSideLane_success.gif"></td><td><img src="../assets/gifs/25439_vad_bev_HazardAtSideLane_success.gif"></td><td> √ </td><td> The ego vehicle detects cyclists, slows down and follows them for a while, and then overtakes them through the leftside of the lane without changing lane.</td>
  </tr>
    <tr>
    <td> 16 </td><td><strong><font color="#add8e6">ORION</font></strong></td> <td>HazardAtSideLane</td><td><img src="../assets/gifs/Orion_rgb/RouteScenario_25439_rep0_Town15_HazardAtSideLane_1_0_03_12_09_06_10.gif"></td><td><img src="../assets/gifs/Orion_bev/RouteScenario_25439_rep0_Town15_HazardAtSideLane_1_0_03_12_09_06_10.gif"></td><td> √ </td><td> ORION detects cyclists and changes lanes to the left to avoid collisions.</td>
  </tr>

</table>


# Emergency Brake

We visualize the behavior of three models on `ParkingCutIn` and `StaticCutIn` scenarios to show their ability of emergency brake. In these scenarios, the ego must slow down or brake to allow a vehicle cut in. 

<table>
  <tr>
    <th> Case ID </th><th> Models </th> <th> Scenario </th><th>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Front&nbsp;Camera&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;</th><th>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;BEV&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;</th><th>Success</th><th>Qualitatively Analysis</th>
  </tr>
  <tr>
    <td> 17 </td><td> TCP-traj </td> <td>ParkingCutIn</td><td><img src="../assets/gifs/18305_tcp_rgb_front_ParkingCutIn_success.gif"></td><td><img src="../assets/gifs/18305_tcp_bev_ParkingCutIn_success.gif"></td> <td> √ </td><td> The ego vehicle brakes and waits the parked vehicle to exit.</td>
  </tr>  <tr>
    <td> 18 </td><td>  UniAD-Base </td> <td>ParkingCutIn</td><td><img src="../assets/gifs/18305_uniad_rgb_front_ParkingCutIn_success.gif"></td><td><img src="../assets/gifs/18305_uniad_bev_ParkingCutIn_success.gif"></td><td> √ </td><td> The ego vehicle detects the parked vehicle, predicts its motion correctly, so the ego vehicle brakes and waits the parked vehicle to exit.</td>
  </tr>
  <tr>
    <td> 19 </td><td>  VAD-Base </td> <td>ParkingCutIn</td><td><img src="../assets/gifs/18305_vad_rgb_front_ParkingCutIn_failed.gif"></td><td><img src="../assets/gifs/18305_vad_bev_ParkingCutIn_failed.gif"></td><td> x </td><td> The ego vehicle detects the parked car but not stops, and leads to a series of collisions.</td>
  </tr>
  <tr>
    <td> 20 </td><td><strong><font color="#add8e6">ORION</font></strong></td> <td>ParkingCutIn<td><img src="../assets/gifs/Orion_rgb/RouteScenario_18305_rep0_Town12_ParkingCutIn_1_0_03_12_07_43_25.gif"></td><td><img src="../assets/gifs/Orion_bev/RouteScenario_18305_rep0_Town12_ParkingCutIn_1_0_03_12_07_43_25.gif"></td><td> √ </td><td> ORION detects the stopped car, correctly predicts its trajectory, and applies the brakes as soon as it sees the car lane change.</td>
  </tr>
  <tr>
    <td> 21 </td><td>  TCP-traj </td> <td>StaticCutIn</td><td><img src="../assets/gifs/26396_tcp_rgb_front_StaticCutIn_failed.gif"></td><td><img src="../assets/gifs/26396_tcp_bev_StaticCutIn_failed.gif"></td> <td> x </td><td> The ego vehicle drives slowly. When the vehicle at front right attempt to change the lane, ego vehicle turns left unnecessaryly, which occurs collision.</td>
  </tr>  
  <tr>
    <td> 22 </td><td>  UniAD-Base </td> <td>StaticCutIn</td><td><img src="../assets/gifs/26396_uniad_rgb_front_StaticCutIn_success.gif"></td><td><img src="../assets/gifs/26396_uniad_bev_StaticCutIn_success.gif"></td><td> √ </td><td> The ego vehicle brakes when other vehicle cuts in.</td>
  </tr>
  <tr>
    <td> 23 </td><td>  VAD-Base </td> <td>StaticCutIn</td><td><img src="../assets/gifs/26396_vad_rgb_front_StaticCutIn_success.gif"></td><td><img src="../assets/gifs/26396_vad_bev_StaticCutIn_success.gif"></td><td> √ </td><td> The ego vehicle stops at several positions that other vehicles may cut in</td>
  </tr>
  <tr>
    <td> 24 </td><td><strong><font color="#add8e6">ORION</font></strong></td> <td>StaticCutIn</td><td><img src="../assets/gifs/Orion_rgb/RouteScenario_26396_rep0_Town05_StaticCutIn_1_15_03_12_18_25_33.gif"></td><td><img src="../assets/gifs/Orion_bev/RouteScenario_26396_rep0_Town05_StaticCutIn_1_15_03_12_18_25_33.gif"></td><td> √ </td><td> ORION detects the stopped car that are about to change lanes and slows down in advance to avoid collisions.</td>
  </tr>

</table>


# Give Way

We visualize the behavior of three models on `YieldToEmergencyVehicle` and `InvadingTurn`  scenarios to show their ability of giving way. In `YieldToEmergencyVehicle`, ego must maneuver to allow the emergency vehicle behind to pass. In `InvadingTurn`,a vehicle coming from the opposite lane invades the ego’s lane, forcing the ego to move right to avoid a possible collision.


<table>
  <tr>
    <th> Case ID </th><th> Models </th> <th> Scenario </th><th>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Front/Back&nbsp;Camera&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;</th><th>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;BEV&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;</th><th>Success</th><th>Qualitatively Analysis</th>
  </tr>
  <tr>
    <td> 25 </td><td> TCP-traj </td> <td>YieldTo<br>Emergency<br>Vehicle</td><td><img src="../assets/gifs/3378_tcp_rgb_front_YieldToEmergencyVehicle_failed.gif"><br><img src="../assets/gifs/3378_tcp_rgb_back_YieldToEmergencyVehicle_failed.gif"></td><td><img src="../assets/gifs/3378_tcp_bev_YieldToEmergencyVehicle_failed.gif"></td> <td> x </td><td> TCP model does not use back cameras, so ego can not detect the emergency vehicle behind.</td>
  </tr>  <tr>
    <td> 26 </td><td>  UniAD-Base </td> <td>YieldTo<br>Emergency<br>Vehicle</td><td><img src="../assets/gifs/3378_uniad_rgb_front_YieldToEmergencyVehicle_failed.gif"><br><img src="../assets/gifs/3378_uniad_rgb_back_YieldToEmergencyVehicle_failed.gif"></td><td><img src="../assets/gifs/3378_uniad_bev_YieldToEmergencyVehicle_failed.gif"></td><td> x </td><td> The ego vehicle fails to detect the emergency vehicle, and does not giveway.</td>
  </tr>
  <tr>
    <td> 27 </td><td>  VAD-Base </td> <td>YieldTo<br>Emergency<br>Vehicle</td><td><img src="../assets/gifs/3378_vad_rgb_front_YieldToEmergencyVehicle_failed.gif"><br><img src="../assets/gifs/3378_vad_rgb_back_YieldToEmergencyVehicle_failed.gif"></td><td><img src="../assets/gifs/3378_vad_bev_YieldToEmergencyVehicle_failed.gif"></td><td> x </td><td> The ego vehicle detects the emergency vehicle and tries to move right to giveway, but collides against vehicle on right lane.</td>
  </tr>
  <tr>
    <td> 28 </td><td><strong><font color="#add8e6">ORION</font></strong></td> <td>YieldTo<br>Emergency<br>Vehicle</td><td><img src="../assets/gifs/Orion_rgb/RouteScenario_3378_rep0_Town13_YieldToEmergencyVehicle_1_19_03_12_19_27_08.gif"><br><img src="../assets/gifs/Orion_rgb/RouteScenario_3378_rep0_Town13_YieldToEmergencyVehicle_1_19_03_12_19_27_08_back.gif"></td><td><img src="../assets/gifs/Orion_bev/RouteScenario_3378_rep0_Town13_YieldToEmergencyVehicle_1_19_03_12_19_27_08.gif"></td><td> x </td><td> ORION detects the emergency vehicle and tries to change lanes to the right. But there were too many cars in the right lane, causing the lane change to fail. </td>
  </tr>
  <tr>
    <td> 29 </td><td>  TCP-traj </td> <td>InvadingTurn</td><td><img src="../assets/gifs/2802_tcp_rgb_front_InvadingTurn_success.gif"></td><td><img src="../assets/gifs/2802_tcp_bev_InvadingTurn_success.gif"></td> <td> √ </td><td> The ego vehicle drives slowly and moves right to avoid collision.</td>
  </tr>  
  <tr>
    <td> 30 </td><td>  UniAD-Base </td> <td>InvadingTurn</td><td><img src="../assets/gifs/2802_uniad_rgb_front_InvadingTurn_success.gif"></td><td><img src="../assets/gifs/2802_uniad_bev_InvadingTurn_success.gif"></td><td> √ </td><td> The ego vehicle drives in a normal spped and moves right to avoid collision.</td>
  </tr>
  <tr>
    <td> 31 </td><td>  VAD-Base </td> <td>InvadingTurn</td><td><img src="../assets/gifs/2802_vad_rgb_front_InvadingTurn_failed.gif"></td><td><img src="../assets/gifs/2802_vad_bev_InvadingTurn_failed.gif"></td><td> x </td><td> The ego vehicle moves too much, it invades the right lane and collides against other vehicle.</td>
  </tr>
  <tr>
    <td> 32 </td><td><strong><font color="#add8e6">ORION</font></strong></td> <td>InvadingTurn</td><td><img src="../assets/gifs/Orion_rgb/RouteScenario_2802_rep0_Town12_InvadingTurn_1_14_03_12_20_16_05.gif"></td><td><img src="../assets/gifs/Orion_bev/RouteScenario_2802_rep0_Town12_InvadingTurn_1_14_03_12_20_16_05.gif"></td><td> √ </td><td> ORION changes lanes to the right at normal speeds and avoids collisions. </td>
  </tr>

</table>


# Traffic Sign

We visualize the behavior of three models on  `EnterActorFlow` and `VanillaNonSignalizedTurnEncounterStopsign` scenarios to show their ability of following traffic sign. In `EnterActorFlow`, ego should follow the traffic light. In `VanillaNonSignalizedTurnEncounterStopsign`, ego should stop and start at stop signs.

<table>
  <tr>
    <th> Case ID </th><th> Models </th> <th> Scenario </th><th>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Front&nbsp;Camera&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;</th><th>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;BEV&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;</th><th>Success</th><th>Qualitatively Analysis</th>
  </tr>
  <tr>
    <td> 33 </td><td> TCP-traj </td> <td>EnterActorFlow</td><td><img src="../assets/gifs/3749_tcp_rgb_front_EnterActorFlow_success.gif"></td><td><img src="../assets/gifs/3749_tcp_bev_EnterActorFlow_success.gif"></td> <td> √ </td><td> The ego vehicle follows the traffic light and goes through the junction.</td>
  </tr>  <tr>
    <td> 34 </td><td>  UniAD-Base </td> <td>EnterActorFlow</td><td><img src="../assets/gifs/3749_uniad_rgb_front_EnterActorFlow_failed.gif"></td><td><img src="../assets/gifs/3749_uniad_bev_EnterActorFlow_failed.gif"></td><td> x </td><td> The ego vehicle detects the traffic light but runs a red light.</td>
  </tr>
  <tr>
    <td> 35 </td><td>  VAD-Base </td> <td>EnterActorFlow</td><td><img src="../assets/gifs/3749_vad_rgb_front_EnterActorFlow_failed.gif"></td><td><img src="../assets/gifs/3749_vad_bev_EnterActorFlow_failed.gif"></td><td>x </td><td> The ego vehicle does not detects the traffic light accurately，and runs a red light.</td>
  </tr>
  <tr>
    <td> 36 </td><td><strong><font color="#add8e6">ORION</font></strong></td> <td>Signalized<br>Junction<br>LeftTurn</td><td><img src="../assets/gifs/Orion_rgb/RouteScenario_3749_rep0_Town13_EnterActorFlow_1_0_03_12_21_29_17.gif"></td><td><img src="../assets/gifs/Orion_bev/RouteScenario_3749_rep0_Town13_EnterActorFlow_1_0_03_12_21_29_17.gif"></td><td> √ </td><td> ORION detects the red traffic light and stops, and goes straight when the light turns green.</td>
  </tr>
  <tr>
    <td> 37 </td><td>  TCP-traj </td> <td>Vanilla<br>NonSignalized<br>TurnEncounter<br>Stopsign</td><td><img src="../assets/gifs/3905_tcp_rgb_front_VanillaNonSignalizedTurnEncounterStopsign_success.gif"></td><td><img src="../assets/gifs/3905_tcp_bev_VanillaNonSignalizedTurnEncounterStopsign_success.gif"></td> <td> √ </td><td> The ego vehicle stops and waits at stop sign.After the opposite vehicle passes the junction, ego goes through the junction.</td>
  </tr>  
  <tr>
    <td> 38 </td><td>  UniAD-Base </td> <td>Vanilla<br>NonSignalized<br>TurnEncounter<br>Stopsign</td><td><img src="../assets/gifs/3905_uniad_rgb_front_VanillaNonSignalizedTurnEncounterStopsign_failed.gif"></td><td><img src="../assets/gifs/3905_uniad_bev_VanillaNonSignalizedTurnEncounterStopsign_failed.gif"></td><td> x </td><td> The ego vehicle does not stop and runs a stop.</td>
  </tr>
  <tr>
    <td> 39 </td><td>  VAD-Base </td> <td>Vanilla<br>NonSignalized<br>TurnEncounter<br>Stopsign</td><td><img src="../assets/gifs/3905_vad_rgb_front_VanillaNonSignalizedTurnEncounterStopsign_failed.gif"></td><td><img src="../assets/gifs/3905_vad_bev_VanillaNonSignalizedTurnEncounterStopsign_failed.gif"></td><td> x </td><td> The ego vehicle stops at the sign but gets blocked, does not start again.</td>
  </tr>
  <tr>
    <td> 40 </td><td><strong><font color="#add8e6">ORION</font></strong></td> <td>Vanilla<br>NonSignalized<br>TurnEncounter<br>Stopsign</td><td><img src="../assets/gifs/Orion_rgb/RouteScenario_3905_rep0_Town13_VanillaNonSignalizedTurnEncounterStopsign_1_0_03_12_07_43_43.gif"></td><td><img src="../assets/gifs/Orion_bev/RouteScenario_3905_rep0_Town13_VanillaNonSignalizedTurnEncounterStopsign_1_0_03_12_07_43_43.gif"></td><td> √ </td><td> ORION recognizes the stop sign and stops, waits for a period of time, and then restarts successfully through the intersection.</td>
  </tr>

</table>

# Conclusion
After comparative analysis, we found that our ORION model can generate high-quality trajectories in complex scenarios, fully demonstrating its great potential.
