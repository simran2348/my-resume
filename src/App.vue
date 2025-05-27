<template>
  <div class="d-flex flex-direction-column align-items-center">
    <button
      class="bg-primary text-white p-10 mb-20 cursor-pointer"
      @click="exportToPDF"
    >
      Download as PDF
    </button>

    <div id="resume" class="resume d-flex flex-direction-column bg-white">
      <div class="resume-page">
        <section class="d-flex justify-center">
          <span class="font-20 font-bold">{{ name }}</span>
        </section>
        <section class="d-flex justify-center align-items-center gap-20 mt-15">
          <div
            v-for="item in socials"
            class="d-flex font-12 align-items-center gap-5"
          >
            <img
              v-if="item.id === 1"
              :id="item.id"
              src="data:image/svg+xml,%3Csvg%20xmlns%3D%22http://www.w3.org/2000/svg%22%20viewBox%3D%220%200%20384%20512%22%20height%3D%2210%22%20width%3D%2210%22%3E%3Cpath%20d%3D%22M215.7%20499.2C267%20435%20384%20279.4%20384%20192C384%2086%20298%200%20192%200S0%2086%200%20192c0%2087.4%20117%20243%20168.3%20307.2c12.3%2015.3%2035.1%2015.3%2047.4%200zM192%20128a64%2064%200%201%201%200%20128%2064%2064%200%201%201%200-128z%22/%3E%3C/svg%3E"
              alt="SVG Image"
            />
            <img
              v-else-if="item.id === 2"
              :id="item.id"
              src="data:image/svg+xml,%3Csvg%20xmlns%3D%22http://www.w3.org/2000/svg%22%20viewBox%3D%220%200%20512%20512%22%20height%3D%2210%22%20width%3D%2210%22%3E%3Cpath%20d%3D%22M48%2064C21.5%2064%200%2085.5%200%20112c0%2015.1%207.1%2029.3%2019.2%2038.4L236.8%20313.6c11.4%208.5%2027%208.5%2038.4%200L492.8%20150.4c12.1-9.1%2019.2-23.3%2019.2-38.4c0-26.5-21.5-48-48-48L48%2064zM0%20176L0%20384c0%2035.3%2028.7%2064%2064%2064l384%200c35.3%200%2064-28.7%2064-64l0-208L294.4%20339.2c-22.8%2017.1-54%2017.1-76.8%200L0%20176z%22/%3E%3C/svg%3E"
              alt="SVG Image"
            />
            <img
              v-else-if="item.id === 3"
              :id="item.id"
              src="data:image/svg+xml,%3Csvg%20xmlns%3D%22http%3A//www.w3.org/2000/svg%22%20viewBox%3D%220%200%20512%20512%22%20height%3D%2210%22%20width%3D%2210%22%3E%3Cpath%20d%3D%22M164.9%2024.6c-7.7-18.6-28-28.5-47.4-23.2l-88%2024C12.1%2030.2%200%2046%200%2064C0%20311.4%20200.6%20512%20448%20512c18%200%2033.8-12.1%2038.6-29.5l24-88c5.3-19.4-4.6-39.7-23.2-47.4l-96-40c-16.3-6.8-35.2-2.1-46.3%2011.6L304.7%20368C234.3%20334.7%20177.3%20277.7%20144%20207.3L193.3%20167c13.7-11.2%2018.4-30%2011.6-46.3l-40-96z%22/%3E%3C/svg%3E"
              alt="SVG Image"
            />
            <img
              v-else
              :id="item.id"
              alt="LinkedIn Icon"
              src="data:image/svg+xml,%3Csvg%20xmlns%3D%22http%3A//www.w3.org/2000/svg%22%20height%3D%2210%22%20width%3D%2210%22%20viewBox%3D%220%200%20448%20512%22%3E%3Cpath%20d%3D%22M416%2032H31.9C14.3%2032%200%2046.5%200%2064.3v383.4C0%20465.5%2014.3%20480%2031.9%20480H416c17.6%200%2032-14.5%2032-32.3V64.3c0-17.8-14.4-32.3-32-32.3zM135.4%20416H69V202.2h66.5V416zm-33.2-243c-21.3%200-38.5-17.3-38.5-38.5S80.9%2096%20102.2%2096c21.2%200%2038.5%2017.3%2038.5%2038.5%200%2021.3-17.2%2038.5-38.5%2038.5zm282.1%20243h-66.4V312c0-24.8-.5-56.7-34.5-56.7-34.6%200-39.9%2027-39.9%2054.9V416h-66.4V202.2h63.7v29.2h.9c8.9-16.8%2030.6-34.5%2062.9-34.5%2067.2%200%2079.7%2044.3%2079.7%20101.9V416z%22/%3E%3C/svg%3E"
            />
            <a
              v-if="item.link"
              :href="item.link"
              class="cursor-pointer"
              target="_blank"
              rel="noopener noreferrer"
              >{{ item.label }}</a
            >
            <span v-else>{{ item.label }}</span>
          </div>
        </section>
        <section class="d-flex flex-direction-column mt-30">
          <span class="font-18">SUMMARY</span>
          <span class="h-divider mt-5" />
          <span class="mt-10 font-12">{{ summary }}</span>
        </section>
        <section class="d-flex flex-direction-column mt-30">
          <span class="font-18">EXPERIENCE</span>
          <span class="h-divider mt-5" />
          <div class="d-flex flex-direction-column mt-10">
            <div
              v-for="item in careerExperience"
              class="d-flex flex-direction-column"
            >
              <span class="font-14 font-bold">{{ item.companyName }}</span>
              <div class="d-flex font-12 justify-between font-bold">
                <span>{{ item.position }}</span>
                <span
                  >{{ item.from }} - {{ item.to }}, {{ item.location }}</span
                >
              </div>
              <ul class="mv-10 ph-25 font-12">
                <li v-for="point in item.experience">
                  {{ point }}
                </li>
              </ul>
            </div>
          </div>
        </section>
        <section class="d-flex flex-direction-column mt-30">
          <span class="font-18 font-weight-500">SKILLS</span>
          <span class="h-divider mt-5" />
          <div class="d-flex flex-direction-column">
            <ul class="mv-10 ph-25 font-12">
              <li v-for="skill in Object.keys(skills)">
                <span class="font-bold">{{ skill }}:</span>
                {{ skills[skill].join(", ") }}
              </li>
            </ul>
          </div>
        </section>
      </div>
      <div class="resume-page">
        <section class="d-flex flex-direction-column">
          <span class="font-18">CERTIFICATIONS</span>
          <span class="h-divider mt-5" />
          <div class="d-flex flex-direction-column mt-10 gap-15">
            <div
              v-for="item in certificates"
              class="d-flex flex-direction-column"
            >
              <span class="font-14 font-bold">{{ item.title }}</span>
              <span class="font-12">{{ item.issuer }} • {{ item.year }}</span>
            </div>
          </div>
        </section>
        <section class="d-flex flex-direction-column mt-30">
          <span class="font-18">EDUCATION</span>
          <span class="h-divider mt-5" />
          <div class="d-flex flex-direction-column mt-10 gap-15">
            <div
              v-for="item in academicsJourney"
              class="d-flex flex-direction-column"
            >
              <span class="font-14 font-bold">{{ item.field }}</span>
              <span class="font-12"
                >{{ item.institution }}, {{ item.country }} • {{ item.to }} •
                {{ item.marks }}</span
              >
            </div>
          </div>
        </section>
      </div>
    </div>
  </div>
</template>

<script setup>
import {
  academicsJourney,
  careerExperience,
  certificates,
  name,
  skills,
  socials,
  summary,
} from "./constant";

import jsPDF from "jspdf";

const replaceSvgImgsWithPng = async () => {
  const svgImgs = document.querySelectorAll("img[src^='data:image/svg+xml']");

  const promises = Array.from(svgImgs).map(async (img) => {
    const canvas = document.createElement("canvas");
    const ctx = canvas.getContext("2d");
    const tempImg = new Image();
    const scale = 3;

    tempImg.crossOrigin = "anonymous";
    tempImg.src = img.src;
    tempImg.id = img.id;

    return new Promise((resolve) => {
      tempImg.onload = () => {
        const width = (tempImg.width || 12) * scale;
        const height = (tempImg.height || 12) * scale;
        canvas.width = width;
        canvas.height = height;
        ctx.drawImage(tempImg, 0, 0, width, height);

        const pngDataUrl = canvas.toDataURL("image/png");
        img.src = pngDataUrl;

        img.style.width = `${width / scale}px`;
        img.style.height = `${height / scale}px`;
        img.style.marginTop = img.id === "4" || img.id === "2" ? "3px" : "1px";
        resolve();
      };
      tempImg.onerror = () => {
        console.error("Failed to load SVG image", img.src);
        resolve();
      };
    });
  });

  await Promise.all(promises);
};

// const exportToPDF = async () => {
//   await replaceSvgImgsWithPng();

//   const doc = new jsPDF({
//     orientation: "portrait",
//     unit: "px",
//     format: [794, 1123],
//   });

//   const resume = document.querySelector(".resume");

//   await doc.html(resume, {
//     x: 0,
//     y: 0,
//     html2canvas: {
//       scale: 1,
//       useCORS: true,
//     },
//     callback: function () {
//       const linkElement = document.querySelector('a[href*="linkedin.com"]');
//       if (linkElement) {
//         const rect = linkElement.getBoundingClientRect();
//         console.log(rect);

//         const offsetX = rect.left;
//         const offsetY = rect.top;
//         const width = rect.width;
//         const height = rect.height;

//         doc.link(offsetX, offsetY, width, height, {
//           url: linkElement.href,
//         });
//       }

//       // doc.save("Simranjit_Singh_Resume.pdf");
//     },
//   });
// };

const exportToPDF = async () => {
  await replaceSvgImgsWithPng();

  const doc = new jsPDF({
    orientation: "portrait",
    unit: "px",
    format: [794, 1123],
  });

  const resume = document.querySelector(".resume");

  await doc.html(resume, {
    x: 0,
    y: 0,
    html2canvas: {
      scale: 1,
      useCORS: true,
    },
  });
  doc.setPage(1);
  doc.setTextColor(0, 0, 0);
  doc.setFontSize(16);
  doc.textWithLink("simranjit-singh-87aa8b152", 553, 101.5, {
    url: "https://www.linkedin.com/in/simranjit-singh-87aa8b152",
  });

  doc.save("Simranjit_Singh_Resume.pdf");
};
</script>
