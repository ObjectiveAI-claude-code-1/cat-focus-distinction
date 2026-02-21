# cat-focus-distinction

Scores how sharply a cat is rendered compared to everything else in a photograph. Evaluates the cat's own sharpness, the softness of its surroundings, and the magnitude of the focus gap between the two, producing a scalar from 0.0 to 1.0. High scores mean the cat commands visual attention through focus; low scores mean it does not.

## Input

The function accepts a single required field:

| Field | Type | Required | Description |
|-------|------|----------|-------------|
| `image` | image | Yes | A photograph containing a cat. May be of any quality, lighting condition, or composition. |

The image is the totality of the input. The function meets each photograph where it is — professional DSLR portrait, hasty phone snapshot, studio composition, or anything in between. It evaluates what the photograph *is*, not what it could have been. No additional parameters, flags, or configuration are needed; the three evaluations the function performs are all derived from analyzing the single image.

## Output

A scalar score between **0.0** and **1.0**.

| Score Range | Interpretation |
|-------------|----------------|
| **0.8 – 1.0** | The cat is the crispest element in the frame with a stark, unmistakable focus differential over its surroundings. The eye has nowhere to go but the cat. |
| **0.5 – 0.8** | The cat is sharper than its surroundings, but the gap is moderate. The cat has a focus advantage, though not a commanding one. |
| **0.3 – 0.5** | The cat is only marginally sharper than its environment, or sharpness is inconsistent. The focus hierarchy is weak. |
| **0.0 – 0.3** | The cat is out of focus, softer than its surroundings, or indistinguishable in sharpness from the rest of the scene. Focus does not favor the cat. |

An equalized (neutral) evaluation produces a score of approximately **0.5**, representing an image where no clear focus distinction can be determined in either direction.

## What It Evaluates

The score emerges from three distinct evaluations, each targeting one dimension of the focus relationship between the cat and its environment.

### 1. Subject Clarity

How sharp is the cat itself? This evaluation isolates the cat as a visual element and assesses the crispness of its fur, whiskers, ears, eyes, and body. It considers the cat as a *complete subject* — a photograph where only the eyes are sharp but the body is soft is not the same as one where the entire cat is uniformly crisp. Subject clarity is the foundation: a cat that is itself blurry cannot, by definition, enjoy a focus advantage.

### 2. Environmental Recession

How soft are the surroundings? This evaluation turns away from the cat and examines everything else — background, foreground, furniture, foliage, textures, patterns, and all non-cat elements. It assesses the degree to which the environment has become blurred, indistinct, and visually subordinate. A background that dissolves into smooth bokeh is actively deferring to the subject; a background that remains sharp and detailed is competing for the viewer's attention.

### 3. The Distinction Gap

How wide is the difference between the cat's sharpness and the environment's softness? This is the defining evaluation — the one that gives the function its name. It measures the *magnitude* of the focus differential. A narrow gap (cat slightly sharper than background) produces a weak sense of distinction. A wide gap (cat is the sole island of crispness in a sea of softness) produces an unmistakable sense of visual priority. When the gap is inverted — the surroundings are sharper than the cat — the score reflects that focus is working *against* the cat.

## Use Cases

- **Photo curation**: Surface the images in a collection where the cat truly pops — where autofocus locked on whiskers rather than chair legs. Filter thousands of cat photos down to the ones with the strongest focus distinction.

- **Multi-dimensional image scoring**: Use as one axis in a broader quality evaluation system alongside composition, lighting, and expression scores. The function answers its own narrow question and composes cleanly with other evaluators.

- **Photography feedback**: Photographers learning depth-of-field control can use the score as a mirror — did focus actually land on the cat, or only seem to? The function reflects what the camera captured, not what the photographer intended.

- **Automated pipelines**: Content platforms, photo competitions, and recommendation systems processing cat imagery at scale can assess focus distinction consistently across thousands of images without human curation.

## What It Does Not Evaluate

This function deliberately limits its scope. It does **not** assess:

- **Overall image quality** — A technically imperfect image with a sharp cat and blurry background scores well.
- **Artistic merit or beauty** — A dreamy, soft-focus portrait where the cat melts into an equally soft meadow may be gorgeous, but scores low because focus offers the viewer no reason to look at the cat over anything else.
- **Composition, lighting, or color** — These dimensions are outside the function's concern.
- **Cat breed, pose, or expression** — The function is indifferent to what the cat is doing; it cares only about how sharply the cat is rendered relative to its surroundings.

## Scoring Philosophy

The function formalizes a deeply intuitive human experience: the feeling of a subject *emerging* from its environment through the authority of being the sharpest thing in the frame. Focus distinction is not an absolute property — it is relational. A cat's visual prominence is defined not by its own sharpness alone, but by the gap between its clarity and the clarity of everything around it. The wider that gap in the cat's favor, the higher the score.