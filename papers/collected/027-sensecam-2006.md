# 027: SenseCam: A Retrospective Memory Aid

**Authors:** Steve Hodges, Lyndsay Williams, Emma Berry, Shahram Izadi, James Srinivasan, Alan Butler, Gavin Smyth, Narinder Kapur, Ken Wood

**Year:** 2006 (UbiComp 2006)

**Topics:** 2.5 (Egocentric Vision and Self-Logging), Others (HCI)

**Source:** Microsoft Research, published in Lecture Notes in Computer Science, vol 4206

---

## Summary

SenseCam is a wearable camera developed by Microsoft Research that automatically captures a continuous visual record of the wearer's day. This seminal work in lifelogging demonstrated the potential for passive image capture to support human memory and autobiographical recall.

### Key Contributions

1. **Hardware Design**: Created a lightweight wearable camera with:
   - Wide-angle (fisheye) lens for broad field of view
   - Automatic image capture triggered by sensors
   - Accelerometer, light sensor, and passive infrared (PIR) detector
   - All-day battery life
   - Compact, unobtrusive form factor

2. **Passive Capture Mechanism**: Camera triggers image capture based on:
   - Significant changes in light level
   - Detected motion via accelerometer
   - Presence of people (via PIR sensor)
   - Regular time intervals (default: every 30 seconds)

3. **Memory Aid Application**: Demonstrated effectiveness for:
   - Supporting autobiographical memory recall
   - Helping patients with memory impairments
   - Enhancing memory for everyday events
   - Providing objective record of experiences

4. **User Studies**: Conducted research showing:
   - Improved recall of past events when reviewing SenseCam images
   - Benefits for patients with amnesia and memory disorders
   - Acceptance and usability of wearable camera technology
   - Privacy considerations and social acceptability

### Relevance to Personal AI Agents

SenseCam is foundational for personal AI agents in several ways:

1. **Passive Data Collection**: Demonstrates feasibility of continuous, passive capture of personal experiences
   - Agents can access rich visual history
   - No manual logging required from users
   - Captures context automatically

2. **Memory Augmentation**: Shows how technology can enhance human memory
   - Visual cues trigger memory recall
   - Objective record supplements subjective memory
   - Foundation for agent-assisted memory retrieval

3. **Sensor Integration**: Early example of multi-modal sensing
   - Combines visual, motion, and environmental data
   - Triggers capture based on contextual changes
   - Model for agent perception systems

4. **Privacy and Social Acceptability**: Addresses key concerns
   - When is passive capture acceptable?
   - How to handle private/sensitive moments?
   - Social reactions to wearable cameras

### Key Insights for Thesis

- **Egocentric Vision Foundation**: One of the first systems to systematically capture first-person perspective
- **Automatic Triggering**: Intelligent sensor-based capture reduces data volume while preserving important moments
- **Memory Science Connection**: Links technology design to cognitive science of memory
- **Clinical Applications**: Demonstrates therapeutic potential for memory-impaired patients
- **Privacy-Utility Trade-off**: Early recognition of the balance between data collection and privacy

### Technical Details

- **Image Resolution**: VGA (640x480)
- **Storage**: ~2,000+ images per day
- **Battery Life: ~12-16 hours
- **Weight: ~170g
- **Sensors: Accelerometer, light sensor, PIR, temperature

### Impact and Legacy

SenseCam influenced:
- Modern body cameras and action cameras (GoPro, etc.)
- Lifelogging research community
- Wearable computing field
- Quantified self movement
- Egocentric vision datasets (Ego4D, EPIC-KITCHENS)

---

## Citation

```bibtex
@inproceedings{hodges2006sensecam,
  title={SenseCam: A retrospective memory aid},
  author={Hodges, Steve and Williams, Lyndsay and Berry, Emma and Izadi, Shahram and Srinivasan, James and Butler, Alan and Smyth, Gavin and Kapur, Narinder and Wood, Ken},
  booktitle={International Conference on Ubiquitous Computing},
  pages={177--193},
  year={2006},
  organization={Springer}
}
```
