<template>
  <div class="pricing-wrap">
    <section class="price-head">
      <div class="head-content">
        <h1>Transparent pricing,<br><span class="yllw">Free to get started</span></h1>
        <p>Get started for FREE, pay for what you use.</p>
      </div>
    </section>
    <section class="pricing-wrap">
      <div class="pricing-table">
        <div class="labels">
          <div class="spacer"></div>
          <div v-for="l in labels" :key="l.index" class="label"><p>{{l}}</p></div>
        </div>
        <div class="plan" v-for="(plan,index) in plans" :key="plan.index">
          <div v-bind:class="{recommend:plan.isRecommend}" class="plan-head">
            <div v-if="plan.isRecommend" class="rec-tag">RECOMMENDED</div>
            <div class="plan-meta">
              <h3 class="plan-name">{{plan.planName}}</h3>
              <h4 class="users">{{plan.users}}</h4>
              <div class="tip">{{plan.tip}}</div>
            </div>
            <div class="plan-prices">
              <h2 class="cost"><div class="strike" v-if="plan.prices.offerCost">{{plan.prices.offerCost}}</div>{{plan.prices.cost}}</h2>
              <div class="billing tip">{{plan.prices.billing}}</div>
            </div>
            <div class="CTA-button">{{plan.btnText}}</div>
            <div class="feat-button" @click="activeFeature[index]=!activeFeature[index]">
              <p v-if="!activeFeature[index]">Show features</p>
              <p v-if="activeFeature[index]">Hide features</p>
            </div>
          </div>
          <div v-bind:class="{active:activeFeature[index]}" class="features">
            <div v-for="f in plan.features" :key="f.index" class="feat basic">
              <p style="white-space: pre;" class="fname">{{f.name}}</p>
              <div style="white-space: pre;" v-if="f.tip" class="ftip tip">{{f.tip}}</div>
            </div>
            <div v-if="plan.proFeatures" class="profeatures">
              <div class="tag">PRO</div>
              <div v-for="f in plan.proFeatures" :key="f.index" class="feat pro">
                <p style="white-space: pre;" class="fname">{{f.name}}</p>
                <div style="white-space: pre;" v-if="f.tip" class="ftip tip">{{f.tip}}</div>
              </div>
            </div>
            <div v-if="plan.addOns" class="addOns-wrap">
              <div class="tag">ADD-ONS+</div>
              <div v-for="f in plan.addOns" :key="f.index" class="feat addOn">
                <p style="white-space: pre;" class="fname">{{f.name}}</p>
                <div style="white-space: pre;" v-if="f.tip" class="ftip tip">{{f.tip}}</div>
                <div v-if="f.iterables" class="iters-wrap">
                  <p style="white-space: pre;" class="iters" v-for="i in f.iterables" :key="i.id"><b>{{i}}</b></p>
                </div>
              </div>
            </div>
            <div v-if="plan.enterpriseFeatures" class="enterpriseFeatures">
              <div class="tag">ENTERPRISE</div>
              <div v-for="f in plan.enterpriseFeatures" :key="f.index" class="feat enterprise">
                <p style="white-space: pre;" class="fname">{{f.name}}</p>
                <div style="white-space: pre;" v-if="f.tip" class="ftip tip">{{f.tip}}</div>
              </div>
            </div>
          </div>
        </div>
        <div class="proUnlock">
          <h3>Get Pro to unlock</h3>
          <div v-for="u in proUnlockFeatures" :key="u.index" class="unlock-feature">
            <div class="icon"></div>
            <p class="text">{{u}}</p>
          </div>
          <div class="arrow"></div>
        </div>
        <div class="enterpriseUnlock">
          <h3>Get Enterprise to unlock</h3>
          <div class="unlock-feature">
            <div class="icon"></div>
            <div class="text">
              <h4>Customisable features</h4>
              <p>for large design teams and content-first companies</p>
            </div>
          </div>
          <div class="arrow"></div>
        </div>
      </div>
    </section>
    <section class="faq-wrap">
      <div class="faq">
        <div class="faq-head">
          <h1>Frequently Asked Questions</h1>
          <p>Still haven't found what you're looking for?<br><a href="#">Send us a messsage</a></p>
        </div>
        <div class="ques-wrap">
          <div v-for="(f,index) in faqs" :key="f.id" class="faqs">
            <div class="ques" @click="activeFaq[index]=!activeFaq[index]" v-bind:class="{activeQ:activeFaq[index]}"><p>{{f.question}}</p></div>
            <div v-if="activeFaq[index]" class="ans"><p>{{f.ans}}</p></div>
          </div>
        </div>
      </div>
    </section>
  </div>
</template>

<script>
export default {
  data(){
    return{
      plans:[
        {
          planName:"Starter",
          users:"Single User Access",
          tip:"Perfect for small-store marketers",
          prices:{
            cost: "$0",
            offerCost: "$49",
            billing: "Billed Monthly"
          },
          btnText:"Try Now!",
          features:[
            { name: "Pre-created designs"},
            { name: "Auto Contrast Color\nAuto Text Wrap"},
            { name: "Upto 10 exports", tip: "per month FREE"},
            { name: "Last 3 versions"},
            { name: "Universal Search"}
          ]
        },
        {
          isRecommend: true,
          planName:"Pro",
          users:"5-User Access",
          tip:"Perfect for marketers & freelancers",
          prices:{
            cost: "$399",
            billing: "Billed Monthly"
          },
          btnText:"Buy Now",
          features:[
            { name: "1 custom banner design import"},
            { name: "Auto Contrast Color\nAuto Text Wrap\nAuto position"},
            { name: "200 exports included", tip: "Top up as you need them"},
            { name: "Upto Last 10 versions"},
            { name: "Integrated Smart Search", tip:"(search across your asset sources)" }
          ],
          proFeatures:[
            { name:"Out of the box integrations",tip:"(Shuttershock,Cloudinary,\nGoogle Drive, DropBox)"},
            { name:"5 users included",tip:"add more users at $12/mo"}
          ],
          addOns:[
            { name:"+ Add on Video/GIF Support"},
            { name:"+ Add on Auto Quality Check"},
            { name:"+ Add on Bots",iterables:[
              "Auto Gradient","Auto remove bg","Auto resize"
            ]},
            { name:"+ Add on Custom Templates"},
          ]
        },
        {
          planName:"Enterprise",
          users:"5+ User Teams",
          tip:"Perfect for ?",
          prices:{
            cost: "$1299",
            billing: "Billed Monthly"
          },
          btnText:"Contact Us",
          features:[
            { name: "Unlimited design imports"},
            { name: "Unlimited\nAuto edit bots"},
            { name: "Customized tiers for\nlarge scale needs"},
            { name: "Upto Last 10 versions"},
            { name: "Customized Asset\nTaxonomy Builder" }
          ],
          proFeatures:[
            { name:"Everything in Pro\n+ Build custom integrations"},
            { name:"20 users included",tip:"add more with custom plans"},
            { name: "+Video/GIF support"},
            { name: "Automated Quality checks"},
            { name: "Custom Auto edit bot services"},
            { name: "Content Production\nAPI for Live Production", tip:"(with high performance production cluster)"}
          ],
          enterpriseFeatures:[
            {name:"Developers SDK",tip:"Build your own content apps on top of a\nsecure design infrastructure"},
            {name:"Design Insights",tip:"Get detailed creative insights and audits on\nyour assets and designs"},
            {name:"The best enterprise SLA,\nsupprt and Security"}
          ]
        }
      ],
      labels:[
        "Templates","Design Bots","Exports","Version History","Search"
      ],
      proUnlockFeatures:[
        "Integrations","Collaboration","Videos & GIFs","Quality Checks","Add on bots","Custom Templates"
      ],
      activeFeature: {
         0:false,
         1:false,
         2:false
       },
      activeFaq:{
        0:false,
        1:false,
        2:false,
        3:false
      },
      faqs:[
        {
          question:"Which features are included in the free plan?",
          ans:"All starter pack feature are included in the free plan"
        },
        {
          question:"What's the catch?",
          ans:"A big fish!"
        },
        {
          question:"What happens when I run out of credits?",
          ans:"When your included credits expire you will not be able to use the advanced automation features in Kubric until you buy more credits or upgrade to a paid plan"
        },
        {
          question:"Is there a limit to the amount of credits I can buy in the free plan?",
          ans:"Nope. Give us all your money!"
        }
      ]
    }
  },
}
</script>

<style lang="scss" scoped>
// variables
$base-color: #2E2D2D;
$base-light: #F9F9F9;
$yellow: #FFD341;
$yellow-light: #FFFAEA;
$purple: #5C40CF;
$purple-light: #F0F1FC;
$text-color: #1F1F21;
$text-light: #3F3D4C;

//faqs
.faq-wrap{
  background: $base-color;
  color: white;
}
.faq{
  max-width: 90rem;
  margin: 0 auto;
  display: flex;
  flex-wrap: wrap;
  padding: 2rem;
  justify-content: space-between;
}
.ques-wrap{
  width: 50%;
}
.faq-head{
  width: 40%;
  p{
    font-style: italic;
    opacity: 0.7;
  }
}
.faqs{
  border-bottom: 1px solid rgba(191, 191, 196, 0.2);
  .ques{
    margin: 1rem 0;
    cursor: pointer;
  }
  .ans{
    margin: 2rem 0;
  }
  .activeQ{
    color: $yellow;
  }
}
a{
  color: inherit;
}

// pricing table styles
.feat-button{
  display: none;
}
.recommend{
  border: 2px solid $purple !important;
  position: relative;
  .rec-tag{
    background: $purple;
    color: white;
    font-weight: white;
    position: absolute;
    top: 0;
    left: 0;
    width: 100%;
    padding: 1rem 0;
    transform: translateY(-100%);
  }
  .plan-name{
    font-size: 2.441rem;
    // margin: 0.25rem 0;
    display: inline;
    box-sizing: border-box;
    ::after {
        content:"";
        position:absolute;
        width:100%;
        bottom:1px;
        z-index:-1;
        background: black;
        // box-shadow: 0px 0px 8px 2px #000000;
    }
  }
  .CTA-button{
    background: $purple;
    color: white;
  }
}
.arrow{
  background: white;
  width: 3rem;
  height: 3rem;
  position: absolute;
  top: 50%;
  right: -1.5rem;
  border-top: 1px solid rgba(46, 45, 45, 0.13);
  border-right: 1px solid rgba(46, 45, 45, 0.13);
  transform: translateY(-50%) rotate(45deg);
}
.proUnlock{
  border: 1px solid rgba(46, 45, 45, 0.13);
  grid-column: 1/3;
  align-self: center;
  justify-self: center;
  margin-top: -70rem;
  border-left: 10px solid $purple;
  padding: 1rem 2rem;
  position: relative;
}
.enterpriseUnlock{
  border: 1px solid rgba(46, 45, 45, 0.13);
  grid-column: 1/3;
  align-self: center;
  justify-self: center;
  margin-top: -20rem;
  border-left: 10px solid $yellow;
  padding: 1rem 3rem;
  position: relative;
}
.icon{
  width: 1em;
  height: 1rem;
  border: 1px solid $text-color;
  border-radius: 50%;
}
.unlock-feature{
  display: flex;
  align-items: center;
  p{
    padding: 1rem 0;
    display: block;
  }
  .icon{
    margin-right: 1rem;
  }
}
.pricing-wrap{
  color: $text-light;
}
.pricing-table{
  margin: 0 auto;
  max-width: 90rem;
  display: grid;
  grid-template-columns: repeat(4, 1fr);
  grid-template-rows: auto;
  margin-top: -20rem;
}
.plan-head{
  text-align: center;
  padding: 1em;
  border: 1px solid rgba(46, 45, 45, 0.13);
  display: flex;
  flex-direction: column;
  justify-content: space-between;
  height: 22rem;
  box-sizing: border-box;
  background: white;
  border-top: 10px solid $yellow
}
.plan-prices{
  margin: 2rem 0;
}
.plan-prices .cost{
  .strike{
    position: relative;
    display: inline;
    margin-right: 0.25rem ;
  }
}
.strike::after{
  content: '';
  height: 5px;
  width: 100%;
  background: $purple;
  position: absolute;
  top: 50%;
  left: 0;
  transform: rotate(-15deg);
}
.CTA-button{
  border: 2px solid $purple;
  border-radius: 4px;
  font-size: 1.25em;
  padding: 0.65rem;
  color: $purple;
  font-weight: bold;
}
.features{
  text-align: center;
}
.feat{
  padding: 1.5rem 2rem;
  border: 1px solid rgba(46, 45, 45, 0.13);
  height: 3em;
  display: flex;
  flex-direction: column;
  justify-content: space-around;
  align-items: center;
}
.basic:nth-child(2), .label:nth-child(3){
  height: 5rem;
}
.addOn:nth-child(4), .pro:nth-child(6){
  height: 7rem;
}
.basic:nth-child(even){
  background: $base-light;
}
.pro:nth-child(even){
  background: $purple-light;
}
.addOn:nth-child(even){
  background: $purple-light;
}
.enterprise:nth-child(even){
  background: $yellow-light;
}
.profeatures{
  position: relative;
  .tag{
    color: #fff;
    background: $purple;
    font-weight: bold;
    width: fit-content;
    position: absolute;
    padding: .8rem;
    transform: rotate(-90deg);
    transform-origin: top left;
    top: 58px;
    left: -45px;
  }
}
.enterpriseFeatures{
  position: relative;
  .tag{
    color: $text-color;
    background: $yellow;
    font-weight: bold;
    width: fit-content;
    position: absolute;
    padding: .8rem;
    transform: rotate(-90deg);
    transform-origin: top left;
    top: 120px;
    left: -45px;
  }
}
.plan:nth-child(4) .profeatures .tag{
  display: none;
}
.addOns-wrap{
  border: 1px solid $base-color;
  position: relative;
  .tag{
    color: #fff;
    background: #2e2d2d;
    width: fit-content;
    position: absolute;
    padding: .8rem;
    transform: rotate(-90deg);
    transform-origin: top left;
    top: 107px;
    left: -45px;
  }
}
.spacer{
  height: 22rem;
}
.labels{
  justify-self: end;
}
.label{
  padding: 1.5rem 2rem;
  border: 1px solid rgba(46, 45, 45, 0.13);
  height: 3em;
  text-align: right;
  font-weight: bold;
  display: flex;
  flex-direction: column;
  justify-content: center;
}
.label:nth-child(odd){
  background: $base-light;
}
.tip{
  font-style: italic;
  color: $text-light;
  opacity: 0.7;
}
.cost{
  margin: 0;
}

// pricing header styles
.price-head{
  background: $base-color;
  height: 60vh;
}
.head-content{
  margin: 0 auto;
  max-width: 90rem;
  color: white;
  padding: 1em 0.75em;
}
.yllw{
  color: $yellow;
}

// responsive
@media (max-width: 768px){
  .feat-button{
    display: block;
    padding: 0.5rem 0;
    height: 5rem;
    margin: 1rem 0;
  }
  .pricing-table{
    grid-template-columns: 1fr;
    grid-template-rows: 1fr 1fr 1fr;
    margin-top: -5rem;
    grid-gap: 1rem;
    margin: 0 2rem;
  }
  .plan{
    .plan-head{
      box-sizing: content-box;
    }
    .features{
      display: none;
    }
    .active{
      display: block;
    }
  }
  .plan:nth-child(3){
    grid-row: 1/2;
  }
  .labels,.proUnlock,.enterpriseUnlock{
    display: none;
  }
  .ques-wrap{
    width: 100%;
    margin-top: 3rem;
  }
  .faq-head{
    width: 100%;
  }
}
</style>