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
        <div class="plan" v-for="plan in plans" :key="plan.index">
          <div class="plan-head">
            <div class="plan-meta">
              <h3 class="plan-name">{{plan.planName}}</h3>
              <h4 class="users">{{plan.users}}</h4>
              <div class="tip">{{plan.tip}}</div>
            </div>
            <div class="plan-prices">
              <h2 class="cost"><strike v-if="plan.prices.offerCost">{{plan.prices.offerCost}}</strike>{{plan.prices.cost}}</h2>
              <div class="billing tip">{{plan.prices.billing}}</div>
            </div>
            <div class="CTA-button">{{plan.btnText}}</div>
          </div>
          <div class="features">
            <div v-for="f in plan.features" :key="f.index" class="feat basic">
              <p class="fname">{{f.name}}</p>
              <div v-if="f.tip" class="ftip tip">{{f.tip}}</div>
            </div>
            <div v-if="plan.proFeatures" class="profeatures">
              <div class="tag">PRO</div>
              <div v-for="f in plan.proFeatures" :key="f.index" class="feat pro">
                <p class="fname">{{f.name}}</p>
                <div v-if="f.tip" class="ftip tip">{{f.tip}}</div>
              </div>
            </div>
            <div v-if="plan.addOns" class="addOns-wrap">
              <div class="tag">ADD-ONS+</div>
              <div v-for="f in plan.addOns" :key="f.index" class="feat addOn">
                <p class="fname">{{f.name}}</p>
                <div v-if="f.tip" class="ftip tip">{{f.tip}}</div>
              </div>
            </div>
            <div v-if="plan.enterpriseFeatures" class="enterpriseFeatures">
              <div class="tag">ENTERPRISE</div>
              <div v-for="f in plan.enterpriseFeatures" :key="f.index" class="feat enterprise">
                <p class="fname">{{f.name}}</p>
                <div v-if="f.tip" class="ftip tip">{{f.tip}}</div>
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
            { name: "Auto Contrast Color Auto Text Wrap"},
            { name: "Upto 10 exports", tip: "per month FREE"},
            { name: "Last 3 versions"},
            { name: "Universal Search"}
          ]
        },
        {
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
            { name: "Auto Contrast Color Auto Text Wrap Auto position"},
            { name: "200 exports included", tip: "Top up as you need them"},
            { name: "Upto Last 10 versions"},
            { name: "Integrated Smart Search", tip:"(search across your asset sources)" }
          ],
          proFeatures:[
            { name:"Out of the box integrations",tip:"(Shuttershock,Cloudinary,Google Drive, DropBox)"},
            { name:"5 users included",tip:"add more users at $12/mo"}
          ],
          addOns:[
            { name:"+ Add on Video/GIF Support"},
            { name:"+ Add on Auto Quality Check"},
            { name:"+ Add on Bots"},
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
            { name: "Unlimited Auto edit bots"},
            { name: "Customized tiers for large scale needs"},
            { name: "Upto Last 10 versions"},
            { name: "Customized Asset Taxonomy Builder" }
          ],
          proFeatures:[
            { name:"Everything in Pro + Build custom integrations"},
            { name:"20 users included",tip:"add more with custom plans"},
            { name: "+Video/GIF support"},
            { name: "Automated Quality checks"},
            { name: "Custom Auto edit bot services"},
            { name: "Content Production API for Live Production", tip:"(with high performance production cluster)"}
          ],
          enterpriseFeatures:[
            {name:"Developers SDK",tip:"Build your own content apps on top of a secure design infrastructure"},
            {name:"Design Insights",tip:"Get detailed creative insights and audits on your assets and designs"},
            {name:"The best enterprise SLA supprt and Security"}
          ]
        }
      ],
      labels:[
        "Templates","Design Bots","Exports","Version History","Search"
      ],
      proUnlockFeatures:[
        "Integrations","Collaboration","Videos & GIFs","Quality Checks","Add on bots","Custom Templates"
      ]
    }
  }
  
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


// pricing table styles
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
  color: $text-color;
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
}
.plan-prices{
  margin: 2rem 0;
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
}
.label:nth-child(even){
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

</style>