<template>
  <div>
    <div class="map-wrap">
      <!-- Map -->
      <div id="map"></div>
      <a href="https://www.maptiler.com" class="watermark">
        <img
          src="https://api.maptiler.com/resources/logo.svg"
          alt="MapTiler logo"
        />
      </a>
      <div class="map" ref="mapContainer"></div>

      <button id="next" type="button" class="next-button">Next Area</button>

    </div>
  </div>
</template>

<script>
import maplibregl from "maplibre-gl";
import router from "../routers/index";

export default {
  name: "MapView",
  data() {
    return {
      currentIndex: 0,
      popupInfo: null,
      searchTerm: "",
      features: [
        {
          type: "Feature",
          geometry: {
            type: "Polygon",
            coordinates: [
              [
                [111.55072191, -3.0271876],
                [111.52542145, -2.98086716],
                [111.49028192, -2.94998578],
                [111.43405867, -2.92471856],
                [111.38908007, -2.92191106],
                [111.35815728, -2.90787343],
                [111.28787822, -2.93454477],
                [111.20213777, -2.98928921],
                [111.3497238, -3.00894039],
                [111.55072191, -3.0271876],
              ],
            ],
          },
          id: "7d5a22a0-85ad-4604-8867-75f1b3d6e4f6",
          properties: {
            name: "Area A",
            Price: "200",
            buyer: "PT. A",
            Diameter: "284.23248 km\u00b2",
            purchased: "true",
          },
        },
        {
          type: "Feature",
          geometry: {
            type: "Polygon",
            coordinates: [
              [
                [107.69021356, -7.66918242],
                [107.71454986, -7.6658935],
                [107.78313399, -7.68014529],
                [107.83623138, -7.70535881],
                [107.83623138, -7.7327631],
                [107.69021356, -7.66918242],
              ],
            ],
          },
          id: "3b712b43-838c-49ec-9d79-268d311ac642",
          properties: {
            name: "Area B",
            Price: "100",
            buyer: "availabe",
            Diameter: "38.80808 km\u00b2",
            purchased: "false",
          },
        },
        {
          type: "Feature",
          geometry: {
            type: "Polygon",
            coordinates: [
              [
                [106.53675859, -6.01097727],
                [106.62948936, -6.00081333],
                [106.62927165, -6.00175588],
                [106.62921439, -6.00207165],
                [106.62855832, -6.00335458],
                [106.62821887, -6.00427179],
                [106.62836908, -6.00467725],
                [106.62801369, -6.00538147],
                [106.62810086, -6.00556419],
                [106.62804587, -6.00578692],
                [106.62781654, -6.00625107],
                [106.62758185, -6.0066792],
                [106.62728949, -6.0072247],
                [106.62702395, -6.00777553],
                [106.62694885, -6.00794492],
                [106.62725999, -6.00837571],
                [106.62718354, -6.00859978],
                [106.62719964, -6.00887987],
                [106.62701456, -6.00939335],
                [106.62703314, -6.00966314],
                [106.62692765, -6.01052523],
                [106.62678088, -6.01136907],
                [106.62632681, -6.01187537],
                [106.62576726, -6.01225852],
                [106.62546455, -6.01257325],
                [106.62453807, -6.01393708],
                [106.62355655, -6.01502722],
                [106.62318733, -6.01553153],
                [106.62299334, -6.01581632],
                [106.62263769, -6.01621364],
                [106.62234671, -6.01655814],
                [106.62205342, -6.01676025],
                [106.621162, -6.0171392],
                [106.62072784, -6.0176146],
                [106.6202267, -6.01828982],
                [106.62012971, -6.01842762],
                [106.61988722, -6.01868944],
                [106.61958238, -6.01905231],
                [106.6184531, -6.02012714],
                [106.61734921, -6.02096771],
                [106.61697509, -6.0213145],
                [106.6161876, -6.02179909],
                [106.61482968, -6.02249727],
                [106.6141461, -6.02285095],
                [106.61218313, -6.02358587],
                [106.61034025, -6.02406357],
                [106.61017628, -6.02418989],
                [106.60997306, -6.02457572],
                [106.60980216, -6.02466988],
                [106.60773988, -6.02530145],
                [106.60688311, -6.02543466],
                [106.60639583, -6.02545533],
                [106.60610023, -6.0254737],
                [106.60602402, -6.02493859],
                [106.60357145, -6.02548518],
                [106.60352065, -6.0255403],
                [106.60348139, -6.0256092],
                [106.60352989, -6.02602948],
                [106.60347908, -6.0260823],
                [106.60342596, -6.02612135],
                [106.60337747, -6.02616039],
                [106.60335437, -6.02619943],
                [106.60331049, -6.02621091],
                [106.60316308, -6.02629079],
                [106.60265882, -6.02625744],
                [106.60253946, -6.0262161],
                [106.60242011, -6.02612407],
                [106.60226186, -6.02606939],
                [106.6020285, -6.02603605],
                [106.60188232, -6.02606939],
                [106.60181259, -6.02615075],
                [106.60162903, -6.02688627],
                [106.6015137, -6.02713833],
                [106.60135143, -6.02727437],
                [106.60088874, -6.02749576],
                [106.60041802, -6.02760112],
                [106.59965493, -6.02788787],
                [106.59922041, -6.0280199],
                [106.59839965, -6.02819195],
                [106.59791149, -6.02818128],
                [106.59776129, -6.0281546],
                [106.59752928, -6.02818261],
                [106.5969915, -6.02828531],
                [106.59634911, -6.02845202],
                [106.59601517, -6.02859872],
                [106.59569331, -6.02869208],
                [106.59545995, -6.02876277],
                [106.59522794, -6.02912286],
                [106.59511797, -6.02923089],
                [106.59485512, -6.02934692],
                [106.59459628, -6.02936293],
                [106.59438841, -6.02941494],
                [106.59413226, -6.02960966],
                [106.59394719, -6.02980438],
                [106.59364276, -6.02980838],
                [106.59339465, -6.02974703],
                [106.59326054, -6.02976036],
                [106.59316935, -6.02980971],
                [106.5923325, -6.03086199],
                [106.5921595, -6.03094868],
                [106.59196235, -6.03097402],
                [106.59167804, -6.03097135],
                [106.59151979, -6.03094334],
                [106.59139238, -6.03084732],
                [106.59129582, -6.03075663],
                [106.5912234, -6.03075796],
                [106.59103297, -6.03082198],
                [106.59097262, -6.03085265],
                [106.59085728, -6.03092467],
                [106.59078084, -6.03097535],
                [106.59077682, -6.03102336],
                [106.59088813, -6.03114473],
                [106.59081169, -6.03127809],
                [106.59059174, -6.03143947],
                [106.59044288, -6.03149148],
                [106.590349, -6.03147548],
                [106.59021489, -6.03142613],
                [106.58990778, -6.03125542],
                [106.58950143, -6.03137145],
                [106.58934049, -6.03143947],
                [106.58921175, -6.03155817],
                [106.58902533, -6.0319556],
                [106.58901997, -6.03205696],
                [106.5889851, -6.03217166],
                [106.58884965, -6.0323157],
                [106.58862032, -6.03245707],
                [106.58849292, -6.03253709],
                [106.58799537, -6.03277048],
                [106.58791088, -6.03278782],
                [106.58781298, -6.03277715],
                [106.58754207, -6.03268913],
                [106.58736639, -6.03261844],
                [106.58682592, -6.03261444],
                [106.5852128, -6.03249891],
                [106.58329991, -6.03223832],
                [106.5825325, -6.03229416],
                [106.58004312, -6.03185861],
                [106.57878159, -6.03163897],
                [106.57853452, -6.03157568],
                [106.57822382, -6.03142305],
                [106.57817219, -6.03118129],
                [106.57780338, -6.03127065],
                [106.57723744, -6.03123598],
                [106.57708321, -6.0311933],
                [106.57702018, -6.03115062],
                [106.57697458, -6.03112528],
                [106.57688741, -6.03091322],
                [106.57677476, -6.03087455],
                [106.57671977, -6.03086655],
                [106.5766031, -6.03090389],
                [106.57627318, -6.03124665],
                [106.57598753, -6.0314627],
                [106.57591779, -6.03151738],
                [106.5756898, -6.03161874],
                [106.5753733, -6.0317161],
                [106.5750501, -6.0317281],
                [106.5745901, -6.03165208],
                [106.57413144, -6.03153872],
                [106.57364596, -6.03142269],
                [106.57335762, -6.03133867],
                [106.57313366, -6.03125065],
                [106.57226596, -6.03102926],
                [106.57215331, -6.03100258],
                [106.57176976, -6.03084654],
                [106.57151226, -6.03074651],
                [106.57076259, -6.03046777],
                [106.57059495, -6.03045711],
                [106.57031332, -6.03047844],
                [106.5698265, -6.03056113],
                [106.56963069, -6.03058914],
                [106.5694711, -6.03064649],
                [106.56918545, -6.03070384],
                [106.5689816, -6.03070784],
                [106.56860877, -6.03069317],
                [106.56809245, -6.03048511],
                [106.56354735, -6.02864606],
                [106.5634227, -6.02845186],
                [106.56267481, -6.02803866],
                [106.56146573, -6.02737754],
                [106.56156544, -6.02710483],
                [106.5610627, -6.02683625],
                [106.56065967, -6.02622472],
                [106.55711965, -6.02462977],
                [106.55676648, -6.02559666],
                [106.55544105, -6.02513388],
                [106.55525408, -6.02528676],
                [106.55510866, -6.02544791],
                [106.55502556, -6.02558013],
                [106.55495493, -6.02562971],
                [106.55486767, -6.02568343],
                [106.55479288, -6.02571649],
                [106.55451035, -6.02571649],
                [106.55431506, -6.02569169],
                [106.55402422, -6.02564624],
                [106.55360041, -6.02561732],
                [106.55275696, -6.02539419],
                [106.55223759, -6.02522065],
                [106.55175562, -6.02498926],
                [106.5515271, -6.02450581],
                [106.55061716, -6.02407608],
                [106.54949948, -6.02342323],
                [106.54939976, -6.02324142],
                [106.5493873, -6.02311333],
                [106.54806187, -6.02229106],
                [106.54704391, -6.02158861],
                [106.54688187, -6.02148531],
                [106.54679461, -6.02123326],
                [106.54610074, -6.02084072],
                [106.54528637, -6.01998539],
                [106.54377812, -6.01884908],
                [106.54290559, -6.01815903],
                [106.54257734, -6.01786152],
                [106.54243192, -6.01762186],
                [106.54222417, -6.01726237],
                [106.54188347, -6.01694007],
                [106.54145966, -6.01599796],
                [106.54134333, -6.01572938],
                [106.54096107, -6.01542361],
                [106.54086966, -6.01498147],
                [106.54079903, -6.01473768],
                [106.54049156, -6.01458066],
                [106.54035029, -6.01480379],
                [106.54016748, -6.01487404],
                [106.53993895, -6.01484512],
                [106.5393905, -6.01453108],
                [106.53874649, -6.01382449],
                [106.53842655, -6.01365095],
                [106.53819388, -6.01328319],
                [106.53743768, -6.01284106],
                [106.53715099, -6.01267577],
                [106.53696401, -6.01236174],
                [106.53681423, -6.01187302],
                [106.5367445, -6.01138468],
                [106.53671108, -6.01098014],
                [106.53675859, -6.01097727],
              ],
            ],
          },
          id: "9f26b6a3-1191-491c-8a92-be24f3c18081",
          properties: {
            name: "Area C",
            Price: "300",
            buyer: "PT.C",
            Diameter: "21.61579 km\u00b2",
            purchased: "true",
          },
        },
      ],
    };
  },

  computed: {
    filteredFeatures() {
      console.log(this.searchTerm);
      return this.features.filter((feature) => {
        return feature.properties.name
          .toLowerCase()
          .includes(this.searchTerm.toLowerCase());
      });
    },
  },

  methods: {

    searchProperty() {
    const searchTerm = document.getElementById("default-search").value;
    const matchingFeature = this.features.find((feature) => {
      return feature.properties.name.toLowerCase() === searchTerm.toLowerCase();
    });

    if (matchingFeature) {
      const index = this.features.indexOf(matchingFeature);
      this.showPopupWithIndex(index);
    }
  },

    updateMap() {
      const feature = this.features[this.currentIndex];

      if (!feature || !feature.geometry) return;

      const coordinates = feature.geometry.coordinates[0];

      const bounds = coordinates.reduce((bounds, coord) => {
        return bounds.extend(coord);
      }, new maplibregl.LngLatBounds(coordinates[0], coordinates[0]));

      this.map.fitBounds(bounds, { padding: 20 });

      this.showPopupWithIndex(this.currentIndex);
    },

    showPopup() {
      console.log("showPopup function called");
      const filteredFeatures = this.filteredFeatures;
      console.log("Filtered Features:", filteredFeatures);

      if (filteredFeatures.length > 0) {
        const feature = filteredFeatures[0];
        console.log("Selected Feature:", feature);
        this.popupInfo = {
          name: feature.properties.name,
          diameter: feature.properties.Diameter,
          price: feature.properties.Price,
          purchased: feature.properties.purchased,
          buyer: feature.properties.buyer,
        };
      }
    },

    calculatePolygonCenter(coordinates) {
      const sum = coordinates.reduce(
        (acc, coord) => {
          return [acc[0] + coord[0], acc[1] + coord[1]];
        },
        [0, 0]
      );

      const center = [sum[0] / coordinates.length, sum[1] / coordinates.length];

      console.log(center);

      return center;
    },

    showPopupWithIndex(index) {
      if (index < 0 || index >= this.filteredFeatures.length) {
        console.error("Invalid index");
        return;
      }

      this.currentIndex = index;

      const feature = this.filteredFeatures[this.currentIndex];

      const now = new Date();

      const hours = String(now.getHours()).padStart(2, "0");
      const minutes = String(now.getMinutes()).padStart(2, "0");
      const seconds = String(now.getSeconds()).padStart(2, "0");

      const formedTime = `${hours}:${minutes}:${seconds}`;

      console.log("id polygon ", formedTime, index);

      if (this.popup) {
        this.popup.remove();
      }

      if (
        !feature ||
        !feature.geometry ||
        !feature.geometry.coordinates ||
        !feature.properties
      ) {
        console.error("Invalid feature or missing properties");
        return;
      }

      const coordinates = feature.geometry.coordinates[0];
      const center = this.calculatePolygonCenter(coordinates);

      if (!coordinates) {
        console.error("Invalid coordinates");
        return;
      }

      const bounds = coordinates.reduce((bounds, coord) => {
        return bounds.extend(coord);
      }, new maplibregl.LngLatBounds(coordinates[0], coordinates[0]));

      this.map.fitBounds(bounds, { padding: 20 });

      this.popupInfo = {
        name: feature.properties.name,
        diameter: feature.properties.Diameter,
        price: feature.properties.Price,
        purchased: feature.properties.purchased,
        buyer: feature.properties.buyer,
      };

      const popupContent = this.generatePopupContent();

      this.popup = new maplibregl.Popup()
        .setLngLat(center)
        .setHTML(popupContent)
        .addTo(this.map);

      document.getElementById("buy-area").addEventListener("click", () => {
        this.navigateToBuyArea();
      });

      document.getElementById("searchProperty").addEventListener("click", () => {
        this.searchProperty();
      });
    },

    navigateToBuyArea() {
      router.push({ name: "detail" });
    },

    generatePopupContent() {
      let buyButton = "";

      if (this.popupInfo.purchased === "true") {
        buyButton = `<button id='buy-area' class="bg-green-500 hover:bg-green-700 text-white font-bold py-2 px-4 rounded mt-4 mx-auto block" style="display: none;">Buy Area</button>`;
      } else {
        buyButton = `<button id='buy-area' class="bg-green-500 hover:bg-green-700 text-white font-bold py-2 px-4 rounded mt-4 mx-auto block">Buy Area</button>`;
      }

      const popupContent = `
    <form class="mb-4">   
        <label for="default-search" class="mb-2 text-sm font-medium text-gray-900 sr-only dark:text-white">Search</label>
        <div class="relative flex items-center">
            <svg class="w-4 h-4 text-gray-500 dark:text-gray-400 absolute left-3" aria-hidden="true" xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 20 20">
                <path stroke="currentColor" stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="m19 19-4-4m0-7A7 7 0 1 1 1 8a7 7 0 0 1 14 0Z"/>
            </svg>
            <input type="search" id="default-search" class="block w-full p-4 pl-10 text-sm text-gray-900 border border-gray-300 rounded-lg bg-gray-50 focus:ring-blue-500 focus:border-blue-500 dark:bg-gray-700 dark:border-gray-600 dark:placeholder-gray-400 dark:text-white dark:focus:ring-blue-500 dark:focus:border-blue-500" placeholder="Search Area..." required>
            <button id="searchProperty" />
        </div>
    </form>

    <table class="mx-auto mb-4">
        <tr>
            <td class="border p-2">Name</td>
            <td class="border p-2">:</td>
            <td class="border p-2">${this.popupInfo.name}</td>
        </tr>
        <tr>
            <td class="border p-2">Diameter</td>
            <td class="border p-2">:</td>
            <td class="border p-2">${this.popupInfo.diameter}</td>
        </tr>
        <tr>
            <td class="border p-2">Price</td>
            <td class="border p-2">:</td>
            <td class="border p-2">${this.popupInfo.price}</td>
        </tr>
        <tr>
            <td class="border p-2">Purchased</td>
            <td class="border p-2">:</td>
            <td class="border p-2">${
              this.popupInfo.purchased === "true" ? "Yes" : "No"
            }</td>
        </tr>
        ${
          this.popupInfo.purchased && this.popupInfo.purchased !== "Yes"
            ? `<tr>
                <td class="border p-2">Buyer</td>
                <td class="border p-2">:</td>
                <td class="border p-2">${this.popupInfo.buyer}</td>
            </tr>`
            : ""
        }
    </table>
    ${buyButton}
`;

      return popupContent;
    },
  },

  mounted() {
    const key = "7HAWfyw9xM3MO7mHYE0w";
    const initialState = { lng: 107.60981, lat: -6.914744, zoom: 10 };
    const self = this;

    const map = new maplibregl.Map({
      container: "map",
      style: `https://api.maptiler.com/maps/hybrid/style.json?key=${key}`,
      center: [initialState.lng, initialState.lat],
      zoom: initialState.zoom,
      hash: true,
    });

    this.map = map;

    map.on("load", function () {
      map.addSource("polygon_areas", {
        type: "geojson",
        data: {
          type: "FeatureCollection",
          features: [
            {
              type: "Feature",
              geometry: {
                type: "Polygon",
                coordinates: [
                  [
                    [106.53675859, -6.01097727],
                    [106.62948936, -6.00081333],
                    [106.62927165, -6.00175588],
                    [106.62921439, -6.00207165],
                    [106.62855832, -6.00335458],
                    [106.62821887, -6.00427179],
                    [106.62836908, -6.00467725],
                    [106.62801369, -6.00538147],
                    [106.62810086, -6.00556419],
                    [106.62804587, -6.00578692],
                    [106.62781654, -6.00625107],
                    [106.62758185, -6.0066792],
                    [106.62728949, -6.0072247],
                    [106.62702395, -6.00777553],
                    [106.62694885, -6.00794492],
                    [106.62725999, -6.00837571],
                    [106.62718354, -6.00859978],
                    [106.62719964, -6.00887987],
                    [106.62701456, -6.00939335],
                    [106.62703314, -6.00966314],
                    [106.62692765, -6.01052523],
                    [106.62678088, -6.01136907],
                    [106.62632681, -6.01187537],
                    [106.62576726, -6.01225852],
                    [106.62546455, -6.01257325],
                    [106.62453807, -6.01393708],
                    [106.62355655, -6.01502722],
                    [106.62318733, -6.01553153],
                    [106.62299334, -6.01581632],
                    [106.62263769, -6.01621364],
                    [106.62234671, -6.01655814],
                    [106.62205342, -6.01676025],
                    [106.621162, -6.0171392],
                    [106.62072784, -6.0176146],
                    [106.6202267, -6.01828982],
                    [106.62012971, -6.01842762],
                    [106.61988722, -6.01868944],
                    [106.61958238, -6.01905231],
                    [106.6184531, -6.02012714],
                    [106.61734921, -6.02096771],
                    [106.61697509, -6.0213145],
                    [106.6161876, -6.02179909],
                    [106.61482968, -6.02249727],
                    [106.6141461, -6.02285095],
                    [106.61218313, -6.02358587],
                    [106.61034025, -6.02406357],
                    [106.61017628, -6.02418989],
                    [106.60997306, -6.02457572],
                    [106.60980216, -6.02466988],
                    [106.60773988, -6.02530145],
                    [106.60688311, -6.02543466],
                    [106.60639583, -6.02545533],
                    [106.60610023, -6.0254737],
                    [106.60602402, -6.02493859],
                    [106.60357145, -6.02548518],
                    [106.60352065, -6.0255403],
                    [106.60348139, -6.0256092],
                    [106.60352989, -6.02602948],
                    [106.60347908, -6.0260823],
                    [106.60342596, -6.02612135],
                    [106.60337747, -6.02616039],
                    [106.60335437, -6.02619943],
                    [106.60331049, -6.02621091],
                    [106.60316308, -6.02629079],
                    [106.60265882, -6.02625744],
                    [106.60253946, -6.0262161],
                    [106.60242011, -6.02612407],
                    [106.60226186, -6.02606939],
                    [106.6020285, -6.02603605],
                    [106.60188232, -6.02606939],
                    [106.60181259, -6.02615075],
                    [106.60162903, -6.02688627],
                    [106.6015137, -6.02713833],
                    [106.60135143, -6.02727437],
                    [106.60088874, -6.02749576],
                    [106.60041802, -6.02760112],
                    [106.59965493, -6.02788787],
                    [106.59922041, -6.0280199],
                    [106.59839965, -6.02819195],
                    [106.59791149, -6.02818128],
                    [106.59776129, -6.0281546],
                    [106.59752928, -6.02818261],
                    [106.5969915, -6.02828531],
                    [106.59634911, -6.02845202],
                    [106.59601517, -6.02859872],
                    [106.59569331, -6.02869208],
                    [106.59545995, -6.02876277],
                    [106.59522794, -6.02912286],
                    [106.59511797, -6.02923089],
                    [106.59485512, -6.02934692],
                    [106.59459628, -6.02936293],
                    [106.59438841, -6.02941494],
                    [106.59413226, -6.02960966],
                    [106.59394719, -6.02980438],
                    [106.59364276, -6.02980838],
                    [106.59339465, -6.02974703],
                    [106.59326054, -6.02976036],
                    [106.59316935, -6.02980971],
                    [106.5923325, -6.03086199],
                    [106.5921595, -6.03094868],
                    [106.59196235, -6.03097402],
                    [106.59167804, -6.03097135],
                    [106.59151979, -6.03094334],
                    [106.59139238, -6.03084732],
                    [106.59129582, -6.03075663],
                    [106.5912234, -6.03075796],
                    [106.59103297, -6.03082198],
                    [106.59097262, -6.03085265],
                    [106.59085728, -6.03092467],
                    [106.59078084, -6.03097535],
                    [106.59077682, -6.03102336],
                    [106.59088813, -6.03114473],
                    [106.59081169, -6.03127809],
                    [106.59059174, -6.03143947],
                    [106.59044288, -6.03149148],
                    [106.590349, -6.03147548],
                    [106.59021489, -6.03142613],
                    [106.58990778, -6.03125542],
                    [106.58950143, -6.03137145],
                    [106.58934049, -6.03143947],
                    [106.58921175, -6.03155817],
                    [106.58902533, -6.0319556],
                    [106.58901997, -6.03205696],
                    [106.5889851, -6.03217166],
                    [106.58884965, -6.0323157],
                    [106.58862032, -6.03245707],
                    [106.58849292, -6.03253709],
                    [106.58799537, -6.03277048],
                    [106.58791088, -6.03278782],
                    [106.58781298, -6.03277715],
                    [106.58754207, -6.03268913],
                    [106.58736639, -6.03261844],
                    [106.58682592, -6.03261444],
                    [106.5852128, -6.03249891],
                    [106.58329991, -6.03223832],
                    [106.5825325, -6.03229416],
                    [106.58004312, -6.03185861],
                    [106.57878159, -6.03163897],
                    [106.57853452, -6.03157568],
                    [106.57822382, -6.03142305],
                    [106.57817219, -6.03118129],
                    [106.57780338, -6.03127065],
                    [106.57723744, -6.03123598],
                    [106.57708321, -6.0311933],
                    [106.57702018, -6.03115062],
                    [106.57697458, -6.03112528],
                    [106.57688741, -6.03091322],
                    [106.57677476, -6.03087455],
                    [106.57671977, -6.03086655],
                    [106.5766031, -6.03090389],
                    [106.57627318, -6.03124665],
                    [106.57598753, -6.0314627],
                    [106.57591779, -6.03151738],
                    [106.5756898, -6.03161874],
                    [106.5753733, -6.0317161],
                    [106.5750501, -6.0317281],
                    [106.5745901, -6.03165208],
                    [106.57413144, -6.03153872],
                    [106.57364596, -6.03142269],
                    [106.57335762, -6.03133867],
                    [106.57313366, -6.03125065],
                    [106.57226596, -6.03102926],
                    [106.57215331, -6.03100258],
                    [106.57176976, -6.03084654],
                    [106.57151226, -6.03074651],
                    [106.57076259, -6.03046777],
                    [106.57059495, -6.03045711],
                    [106.57031332, -6.03047844],
                    [106.5698265, -6.03056113],
                    [106.56963069, -6.03058914],
                    [106.5694711, -6.03064649],
                    [106.56918545, -6.03070384],
                    [106.5689816, -6.03070784],
                    [106.56860877, -6.03069317],
                    [106.56809245, -6.03048511],
                    [106.56354735, -6.02864606],
                    [106.5634227, -6.02845186],
                    [106.56267481, -6.02803866],
                    [106.56146573, -6.02737754],
                    [106.56156544, -6.02710483],
                    [106.5610627, -6.02683625],
                    [106.56065967, -6.02622472],
                    [106.55711965, -6.02462977],
                    [106.55676648, -6.02559666],
                    [106.55544105, -6.02513388],
                    [106.55525408, -6.02528676],
                    [106.55510866, -6.02544791],
                    [106.55502556, -6.02558013],
                    [106.55495493, -6.02562971],
                    [106.55486767, -6.02568343],
                    [106.55479288, -6.02571649],
                    [106.55451035, -6.02571649],
                    [106.55431506, -6.02569169],
                    [106.55402422, -6.02564624],
                    [106.55360041, -6.02561732],
                    [106.55275696, -6.02539419],
                    [106.55223759, -6.02522065],
                    [106.55175562, -6.02498926],
                    [106.5515271, -6.02450581],
                    [106.55061716, -6.02407608],
                    [106.54949948, -6.02342323],
                    [106.54939976, -6.02324142],
                    [106.5493873, -6.02311333],
                    [106.54806187, -6.02229106],
                    [106.54704391, -6.02158861],
                    [106.54688187, -6.02148531],
                    [106.54679461, -6.02123326],
                    [106.54610074, -6.02084072],
                    [106.54528637, -6.01998539],
                    [106.54377812, -6.01884908],
                    [106.54290559, -6.01815903],
                    [106.54257734, -6.01786152],
                    [106.54243192, -6.01762186],
                    [106.54222417, -6.01726237],
                    [106.54188347, -6.01694007],
                    [106.54145966, -6.01599796],
                    [106.54134333, -6.01572938],
                    [106.54096107, -6.01542361],
                    [106.54086966, -6.01498147],
                    [106.54079903, -6.01473768],
                    [106.54049156, -6.01458066],
                    [106.54035029, -6.01480379],
                    [106.54016748, -6.01487404],
                    [106.53993895, -6.01484512],
                    [106.5393905, -6.01453108],
                    [106.53874649, -6.01382449],
                    [106.53842655, -6.01365095],
                    [106.53819388, -6.01328319],
                    [106.53743768, -6.01284106],
                    [106.53715099, -6.01267577],
                    [106.53696401, -6.01236174],
                    [106.53681423, -6.01187302],
                    [106.5367445, -6.01138468],
                    [106.53671108, -6.01098014],
                    [106.53675859, -6.01097727],
                  ],
                ],
              },
              id: "9f26b6a3-1191-491c-8a92-be24f3c18081",
              properties: {
                name: "Area C",
                Price: "300",
                buyer: "PT.C",
                Diameter: "21.61579 km\u00b2",
                purchased: "true",
              },
            },
            {
              type: "Feature",
              geometry: {
                type: "Polygon",
                coordinates: [
                  [
                    [111.55072191, -3.0271876],
                    [111.52542145, -2.98086716],
                    [111.49028192, -2.94998578],
                    [111.43405867, -2.92471856],
                    [111.38908007, -2.92191106],
                    [111.35815728, -2.90787343],
                    [111.28787822, -2.93454477],
                    [111.20213777, -2.98928921],
                    [111.3497238, -3.00894039],
                    [111.55072191, -3.0271876],
                  ],
                ],
              },
              id: "7d5a22a0-85ad-4604-8867-75f1b3d6e4f6",
              properties: {
                name: "Area A",
                Price: "200",
                buyer: "PT. A",
                Diameter: "284.23248 km\u00b2",
                purchased: "true",
              },
            },
            {
              type: "Feature",
              geometry: {
                type: "Polygon",
                coordinates: [
                  [
                    [107.69021356, -7.66918242],
                    [107.71454986, -7.6658935],
                    [107.78313399, -7.68014529],
                    [107.83623138, -7.70535881],
                    [107.83623138, -7.7327631],
                    [107.69021356, -7.66918242],
                  ],
                ],
              },
              id: "3b712b43-838c-49ec-9d79-268d311ac642",
              properties: {
                name: "Area B",
                Price: "100",
                buyer: "availabe",
                Diameter: "38.80808 km\u00b2",
                purchased: "false",
              },
            },
          ],
        },
      });

      map.addLayer({
        id: "polygons",
        type: "fill",
        source: "polygon_areas",
        layout: {},
        paint: {
          "fill-color": "#748E63",
          "fill-opacity": 0.5,
        },
      });

      map.addLayer({
        id: "outline",
        type: "line",
        source: "polygon_areas",
        layout: {},
        paint: {
          "line-color": "#748E63",
          "line-width": 2,
        },
      });

      map.on("click", "polygons", function (e) {
        this.popupInfo = {
          name: e.features[0].properties.name,
          diameter: e.features[0].properties.Diameter,
          price: e.features[0].properties.Price,
          purchased: e.features[0].properties.purchased,
          buyer: e.features[0].properties.buyer,
        };

        //zoom map
        const coordinates = e.features[0].geometry.coordinates[0];
        const centerLng =
          coordinates.reduce((sum, coord) => sum + coord[0], 0) /
          coordinates.length;
        const centerLat =
          coordinates.reduce((sum, coord) => sum + coord[1], 0) /
          coordinates.length;

        const zoom = 10;
        const pitch = 60;
        const bearing = 30;

        map.easeTo({
          center: [centerLng, centerLat],
          zoom: zoom,
          pitch: pitch,
          bearing: bearing,
          duration: 4000,
          easing: (t) => t,
        });

        const popupContent = `
                <form class="mb-4">   
        <label for="default-search" class="mb-2 text-sm font-medium text-gray-900 sr-only dark:text-white">Search</label>
        <div class="relative flex items-center">
            <svg class="w-4 h-4 text-gray-500 dark:text-gray-400 absolute left-3" aria-hidden="true" xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 20 20">
                <path stroke="currentColor" stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="m19 19-4-4m0-7A7 7 0 1 1 1 8a7 7 0 0 1 14 0Z"/>
            </svg>
            <input type="search" id="default-search" class="block w-full p-4 pl-10 text-sm text-gray-900 border border-gray-300 rounded-lg bg-gray-50 focus:ring-blue-500 focus:border-blue-500 dark:bg-gray-700 dark:border-gray-600 dark:placeholder-gray-400 dark:text-white dark:focus:ring-blue-500 dark:focus:border-blue-500" placeholder="Search Area..." required>
            <button id="searchProperty" />
        </div>
    </form>
  <table class="table-auto border border-collapse mx-auto">
    <tr>
      <td class="border p-2">Name</td>
      <td class="border p-2">:</td>
      <td class="border p-2">${e.features[0].properties.name}</td>
    </tr>
    <tr>
      <td class="border p-2">Diameter</td>
      <td class="border p-2">:</td>
      <td class="border p-2">${e.features[0].properties.Diameter}</td>
    </tr>
    <tr>
      <td class="border p-2">Price</td>
      <td class="border p-2">:</td>
      <td class="border p-2">${e.features[0].properties.Price}</td>
    </tr>
    <tr>
      <td class="border p-2">Purchased</td>
      <td class="border p-2">:</td>
      <td class="border p-2">${
        e.features[0].properties.purchased === "true" ? "Yes" : "No"
      }</td>
    </tr>
    ${
      e.features[0].properties.purchased &&
      e.features[0].properties.purchased !== "Yes"
        ? `
        <tr>
          <td class="border p-2">Buyer</td>
          <td class="border p-2">:</td>
          <td class="border p-2">${e.features[0].properties.buyer}</td>
        </tr>
      `
        : ""
    }
  </table>
  ${
    e.features[0].properties.purchased === "true"
      ? `<button id="buy-area" class="bg-green-500 hover:bg-green-700 text-white font-bold py-2 px-4 rounded mt-4 mx-auto block" style="display:none;">Buy Area</button>`
      : `<button id="buy-area" class="bg-green-500 hover:bg-green-700 text-white font-bold py-2 px-4 rounded mt-4 mx-auto block">Buy Area</button>`
  }
`;

        self.popup = new maplibregl.Popup()
          .setLngLat(e.lngLat)
          .setHTML(popupContent)
          .addTo(map);

          document.getElementById("searchProperty").addEventListener("click", () => {
        self.searchProperty();
      });

        document.getElementById("next").addEventListener("click", () => {
          self.currentIndex++;

          if (self.currentIndex >= self.features.length) {
            self.currentIndex = 0;
          }

          if (self.popup) {
            self.popup.remove();
          }

          self.showPopupWithIndex(self.currentIndex);
          self.showPopup();
        });
      });
    });
  },
};
</script>

<style scoped>
@import url(https://cdn.maptiler.com/maplibre-gl-js/v2.2.0-pre.2/maplibre-gl.css);

.map-wrap {
  position: fixed;
  /* Changed to fixed */
  top: 0;
  left: 0;
  width: 100vw;
  /* Changed to viewport width */
  height: 100vh;
  /* Changed to viewport height */
}

.next-button {
  position: absolute;
  bottom: 20px;
  left: 20px;
  background-color: #007bff;
  color: #fff;
  border: none;
  padding: 10px 20px;
  cursor: pointer;
  border-radius: 5px;
  z-index: 1;
  /* Set a higher z-index */
}

.next-button:hover {
  background-color: #0056b3;
}

#map {
  width: 100%;
  /* Remove fixed width */
  height: 100%;
  /* Remove fixed height */
  z-index: 0;
}

.watermark {
  position: absolute;
  left: 10px;
  bottom: 10px;
  z-index: 700;
}
</style>
