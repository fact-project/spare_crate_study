I had to modifz ratecontrol.cc like this:

~~~
Index: ratecontrol.cc
===================================================================
--- ratecontrol.cc      (revision 18632)
+++ ratecontrol.cc      (working copy)
@@ -726,7 +726,7 @@
             return RateControl::State::kDimNetworkNA;
 
         // All subsystems are not connected
-        if (fDimFTM.state()<FTM::State::kConnected || fDimDrive.state()<Drive::State::kConnected)
+        if (fDimFTM.state()<FTM::State::kConnected )
             return RateControl::State::kDisconnected;
~~~
