# Flux-CI-CD Proposal

We plan to set up a CI/CD pipeline using GitHub, DockerHub, Kubernetes and Flux. This would include automatic testing and image generation, live deployment updates using these images, deployment manifest updates with new version numbers and deployment manifest synchronization between GitHub and the running cluster.

![Flow Diagram](assets/project_diagram-1.png)

![Actor Diagram](assets/project_diagram-2.png)

As shown, the image name would depend on whether a tag was used or not. The kubernetes cluster would only update to versions with the same major version and ignore all non semver named images, i.e. main-j7gjk-12034 would be ingored.

As a basis we would use the deployment demo presented in the lecture. We would update the CI pipeline to produce the naming discussed above. We would then add Flux for manifest synchronization and [Flux image updates](https://fluxcd.io/flux/guides/image-update/) for automatic version updating.

We believe this project should be categorized as advanced, because it extends the project "GitOps" described in the "Project Ideas" pdf by also incorporating automatic image updates.

### Intended Development Usage

This would be intended for usage with [Trunk-based development](https://cloud.google.com/architecture/devops/devops-tech-trunk-based-development) shown in the image below.

![Trunk-based development](https://cloud.google.com/static/architecture/devops/images/devops-tech-trunk-based-development-typical-trunk-timeline.svg)

### Demo

For demo purposes, we could create a new repository and show all steps involved or use an existing repository to demonstrate the (push tag -> generate image -> update manifests -> update deployments) pipeline, or both.

### Work split

| Member      | Tasks |
| ----------- | ----------- |
| Christoph Pfleger | Create Proposal (find resources, check feasibility, design illustrations), Adapting CI pipeline, add basic Flux reconciliation |
| Luis Nachtigall | Discussion on how to implement Proposal with Development workflow, Add image updates (to Kubernetes cluster and GitHub manifests) |

### Extra Ideas

If this is seen as too small or to unrealistic, there is an additional idea we could implement:
- Adding a staging cluster that automatically loads images from normal pushes for testing