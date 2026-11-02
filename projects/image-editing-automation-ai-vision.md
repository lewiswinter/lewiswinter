# Image Editing Automation & AI Vision Experiment

**Production black-and-white image automation, with a separate computer vision cropping experiment**

Photographic production involves repetitive image preparation and quality checks. I tackled two parts of that workload: automating black-and-white versions for customer galleries, and testing whether computer vision could propose crops close to a human editor's choices.

## 1. EditDesk — image automation in production

Preparing black-and-white alternatives had been a repetitive proofing task. I built **EditDesk**, a local processing workflow connected to the **Netlife API**.

The application retrieves the relevant source images, creates black-and-white versions **on the local machine**, and returns the output to the appropriate gallery. Staff can see processing progress and identify exceptions without manually repeating each edit and upload.

**Business results:** the automation **reduced proofing time** and made black-and-white options available more consistently. That supported greater uptake of larger digital packages and **helped increase average order value**.

The workflow is **running in production**. Images are retrieved from and uploaded to the existing gallery platform, but editing takes place locally rather than through an additional cloud image-editing service.

### EditDesk interface

![EditDesk image-processing and gallery workflow](images/ED1.png)

## 2. AI vision — evaluating automated photographic cropping

Cropping required a different approach. Detecting a person correctly is only the starting point; a usable crop also needs the right proportions, headroom and body framing. A high-confidence detection can still cut off feet or leave the subject poorly positioned.

I experimented with open-source computer vision techniques, including:

- **Person and object detection** to locate the subject.
- **Face and body landmarks / pose estimation** to understand head and body position.
- **Scene and composition cues** to account for surrounding space and the intended framing.
- **Candidate crop generation and ranking** to compare several plausible crop positions.
- **Evaluation against reference crops** using geometric overlap and orientation accuracy.

Rather than choosing the first detected bounding box, the experimental pipeline generated crop candidates and evaluated how closely they matched the intended frame.

### Recorded experimental results

| Measure | Result |
| --- | ---: |
| Mean intersection-over-union (IoU) with reference crops | **0.7971** |
| Improvement against the comparison baseline | **+0.0362** |
| Orientation accuracy | **90.7%** |

These are results from a recorded **Stage 5 evaluation**, not a production deployment claim. IoU measures overlap with the reference crop; editorial suitability still needs human judgement.

### Vision comparison

![Computer vision crop experiment with reference and predicted framing](images/EX2.png)

*The comparison illustration uses example confidence values rather than the experimental accuracy results above.*

## Privacy and development approach

**All training and evaluation imagery for the AI vision experiment was synthetic and processed locally.** No customer photographs were used for model training. EditDesk likewise performs its image edits locally, while using the existing Netlife platform for file retrieval and gallery delivery.

The two projects had different purposes: EditDesk removed an established repetitive production step; the cropping work was a measured experiment to determine whether more complex editorial decisions could be automated reliably.

*Source code and customer image records remain private. The screenshots are demonstrations of the workflows.*

---

[← Back to portfolio](../README.md) · [Operations CRM](operations-crm.md) · [Recruitment agent](ai-recruitment-operations-agent.md)
