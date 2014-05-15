Kinect Background Removal (Kinect version 2)
===========================

Background removal (aka "green-screen effect") using Kinect for Windows version 2.

YouTube videos
---
- [Color & image backgrounds] (https://youtube.com/watch?v=Hu6pDb6revs)
- [Video backgrounds] (https://youtube.com/watch?v=s3kD5OPEF0c)

Example usage
---

        void Reader_MultiSourceFrameArrived(object sender, MultiSourceFrameArrivedEventArgs e)
        {
            var reference = e.FrameReference.AcquireFrame();

            var colorFrame = reference.ColorFrameReference.AcquireFrame();
            var depthFrame = reference.DepthFrameReference.AcquireFrame();
            var bodyIndexFrame = reference.BodyIndexFrameReference.AcquireFrame();

            if (colorFrame != null && depthFrame != null && bodyIndexFrame != null)
            {
                // Update the image source.
                camera.Source = _backgroundRemovalTool.GreenScreen(colorFrame, depthFrame, bodyIndexFrame);
            }

            colorFrame.Dispose();
            depthFrame.Dispose();
            bodyIndexFrame.Dispose();
        }
       
