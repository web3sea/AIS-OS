# Priorities

Quarter running to Dec 20, 2026. Set Sep 21, 2026.

1. Launch all three products and reach 30 paying AIOS Coffee users by Dec 20,
   2026. Coffee is the wedge; adoption is expected to spill over into IQ and
   Signals.

   Measured via product-side Stripe (see `connections.md` domain 1). This
   AIOS does not build its own Stripe plumbing; the product side already
   owns the count.

   Dependency: CDP ships first or all three slip together. CDP is the data
   connector layer, IQ sits on CDP, and Coffee and Signals read from IQ, so
   everything is downstream of connectors landing. CDP has to support many
   meeting connectors because users arrive on whichever tool they already use,
   and each user connects one. Running Granola, Fireflies, Wispr Flow and
   Read.ai personally is deliberate connector testing, not tool sprawl (Teams
   is out of scope for this release). The gating artifact is the normalized
   schema every connector maps into, since IQ can only cite what resolves to a
   common shape.
2. Stand up an agent team that autonomously delivers the end-to-end product
   lifecycle workflow.

   Definition of done: agents work through all nine stages without
   intervention.

       intake -> discovery -> intent -> plan -> build -> qa -> uat ->
       feedback -> prod

   Three conditions, all required:

   - Every task is documented as it goes.
   - The client is kept updated along the way in the client dashboard.
   - The "Rabbit" agent converses with the client, returns their feedback, and
     fixes and deploys against that feedback on demand.

   Measurable as stages cleared without human intervention, out of nine.
