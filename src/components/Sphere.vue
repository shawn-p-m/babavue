<script>
import { PBRMaterial, Color3, Mesh } from "@babylonjs/core";
import "@babylonjs/core/Meshes/meshBuilder";

import entity from "@/mixins/entity";
import position from "@/mixins/position";

export default {
  name: "Sphere",
  mixins: [entity, position],
  data: function() {
    return {
      events: []
    };
  },

  methods: {
    addToScene() {
      this.sceneElement = Mesh.CreateSphere(
        this.value.id,
        16,
        1,
        this.babylon.scene
      );

      this.sceneElement.position.x = 0;
      this.sceneElement.position.y = 0.5;
      this.sceneElement.position.z = 0;

      var material = new PBRMaterial("pbr", this.babylon.scene);
      material.albedoColor = new Color3(1.0, 0.766, 0.336);
      material.metallic = 0;
      material.roughness = 0;

      this.sceneElement.material = material;
    },

    removeFromScene() {
      this.sceneElement.dispose();
    }
  }
};
</script>
