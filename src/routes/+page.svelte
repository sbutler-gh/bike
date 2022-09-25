<script>
	let riders = [];


    let riders_options = [
        {
            "value": "kids",
            "label": "Kids",
            // "description": "Organize local in person or virtual meetings, help resistors team up with buddies, enable peer bonding support, create and maintain local afficnity groups, liason with central staff leadership, help create and foster security in your city or neighborhood; remind volunteers and potential volunteers of meetings, and also vet to minimize infiltrators. Training will be offered by central campaign professional staff"
        },
        {
            "value": "immobile",
            "label": "Elderly, immobile, or impaired",
            // "description": "Organize local in person or virtual meetings, help resistors team up with buddies, enable peer bonding support, create and maintain local afficnity groups, liason with central staff leadership, help create and foster security in your city or neighborhood; remind volunteers and potential volunteers of meetings, and also vet to minimize infiltrators. Training will be offered by central campaign professional staff"
        },
        {
            "value": "partner",
            "label": "Partner or spouse",
            // "description": "Organize local in person or virtual meetings, help resistors team up with buddies, enable peer bonding support, create and maintain local afficnity groups, liason with central staff leadership, help create and foster security in your city or neighborhood; remind volunteers and potential volunteers of meetings, and also vet to minimize infiltrators. Training will be offered by central campaign professional staff"
        },
        {
            "value": "friends",
            "label": "Friends, family, relatives",
            // "description": "Organize local in person or virtual meetings, help resistors team up with buddies, enable peer bonding support, create and maintain local afficnity groups, liason with central staff leadership, help create and foster security in your city or neighborhood; remind volunteers and potential volunteers of meetings, and also vet to minimize infiltrators. Training will be offered by central campaign professional staff"
        },
        {
            "value": "pets",
            "label": "Pets!",
            // "description": "Organize local in person or virtual meetings, help resistors team up with buddies, enable peer bonding support, create and maintain local afficnity groups, liason with central staff leadership, help create and foster security in your city or neighborhood; remind volunteers and potential volunteers of meetings, and also vet to minimize infiltrators. Training will be offered by central campaign professional staff"
        },
    ];


    let errands = [];

    let errands_options = [
        {
            "value": "groceries",
            "label": "Grocery shopping",
            // "description": "Organize local in person or virtual meetings, help resistors team up with buddies, enable peer bonding support, create and maintain local afficnity groups, liason with central staff leadership, help create and foster security in your city or neighborhood; remind volunteers and potential volunteers of meetings, and also vet to minimize infiltrators. Training will be offered by central campaign professional staff"
        },
        {
            "value": "kids",
            "label": "Take kids to school and activities",
            // "description": "Organize local in person or virtual meetings, help resistors team up with buddies, enable peer bonding support, create and maintain local afficnity groups, liason with central staff leadership, help create and foster security in your city or neighborhood; remind volunteers and potential volunteers of meetings, and also vet to minimize infiltrators. Training will be offered by central campaign professional staff"
        },
        {
            "value": "short_commute",
            "label": "Short commute to work (< 3 miles)",
            // "description": "Organize local in person or virtual meetings, help resistors team up with buddies, enable peer bonding support, create and maintain local afficnity groups, liason with central staff leadership, help create and foster security in your city or neighborhood; remind volunteers and potential volunteers of meetings, and also vet to minimize infiltrators. Training will be offered by central campaign professional staff"
        },
        {
            "value": "long_commute",
            "label": "Medium-long commute to work",
            // "description": "Organize local in person or virtual meetings, help resistors team up with buddies, enable peer bonding support, create and maintain local afficnity groups, liason with central staff leadership, help create and foster security in your city or neighborhood; remind volunteers and potential volunteers of meetings, and also vet to minimize infiltrators. Training will be offered by central campaign professional staff"
        },
        {
            "value": "activities",
            "label": "Local activities around community",
            // "description": "Organize local in person or virtual meetings, help resistors team up with buddies, enable peer bonding support, create and maintain local afficnity groups, liason with central staff leadership, help create and foster security in your city or neighborhood; remind volunteers and potential volunteers of meetings, and also vet to minimize infiltrators. Training will be offered by central campaign professional staff"
        }
    ];



</script>
<!-- Input options -->
<!-- Output bike -->

<!-- <label>When you think about transportation, are you only thinking about yourself, or do you have any other people in mind?</label> -->


<!-- <label>Do you have any children, dependents, who routinely go places with you?</label> -->
<!-- {#each support_role_options as option}
    // <div class="checkbox"><input type="checkbox" value={option.value} bind:group={support_roles}><label class="support_label">{option.label}</label>
    //     <br>
    // <span class="support_description">{option.description}</span>
    // </div>
    {/each} -->


<label>When thinking about transportation, do you have any chidlren, dependents, or other people (e.g. friends, family, partners) that you routinely take places?</label>
{#each riders_options as rider}
<div class="checkbox"><input type="checkbox" name="riders" bind:group={riders} value={rider.value}><label>{rider.label}</label></div>
{/each}

<!-- <label>Do you have any impairments or conditions that affect your transportation options?</label>
{#each riders_options as rider}
<div class="checkbox"><input type="checkbox" name="riders" bind:group={riders} value={rider.value}><label>{rider.label}</label></div>
{/each} -->

<br>
<label>What are your routine trips and errands?</label>
{#each errands_options as errand}
{#if errand.value == "kids" && !riders.includes('kids')}
{:else}
<div class="checkbox"><input type="checkbox" name="errands" bind:group={errands} value={errand.value}><label>{errand.label}</label></div>
{/if}
{/each}


<!-- <label>How would you be storing your bike?</label>
{#each riders_options as rider}
<div class="checkbox"><input type="checkbox" name="riders" bind:group={riders} value={rider.value}><label>{rider.label}</label></div>
{/each} -->
<!-- Carrying up stairs into my home/apartment -->
<!-- Stored at ground level -->

<!-- <label>How is the terrain in your area?</label>
{#each riders_options as rider}
<div class="checkbox"><input type="checkbox" name="riders" bind:group={riders} value={rider.value}><label>{rider.label}</label></div>
{/each} -->

<footer>
    <hr>
    {#if errands.length < 1 && riders.length < 1}
    <p>Awaiting selection!</p>
    {:else if !errands.includes('groceries') && !errands.includes('long_commute') && riders.length < 1}
    <img src="mini.jpeg">
    {:else if riders.includes('kids')}
    <img src="cargofam.avif">
    {:else if riders.includes('friends') || riders.includes('partner')}
    <img src="gsd.jpeg">
    {:else if errands.includes("long_commute")}
    <img src="long_commute.jpeg">
    {:else if errands.includes('groceries')}
    <img src="groceries.jpeg">
    {/if}
    <!-- {:else if}

    <img src="https://static01.nyt.com/images/2015/04/23/fashion/23CARGOBIKES/23CARGOBIKES-videoSixteenByNine3000.jpg?year=2015&h=1688&w=3000&s=d82ce31872d06cbafcfd95e45e27ebe587132f375d7f608f843b06dded67fbb1&k=ZQJBKqZ0VN&tw=1">
    {:else if errands.includes('groceries') && !riders.includes('kids')}
    <img src="https://r4e7m5h6.stackpathcdn.com/wp-content/uploads/2018/07/best-grocery-panniers-review.jpg">
    {:else if }
    <img src="https://assets.newatlas.com/dims4/default/f77ed89/2147483647/strip/true/crop/5616x3744+0+0/resize/1200x800!/quality/90/?url=http%3A%2F%2Fnewatlas-brightspot.s3.amazonaws.com%2Farchive%2Furbanarrow.jpg">
    
    <img src="https://mediapool.bmwgroup.com/cache/P9/201802/P90295373/P90295373-mini-folding-bike-03-18-2410px.jpg">
    <img src="https://www.premiumbikes.se/wp-content/uploads/2020/09/GSD-G2-easytomanage.jpg">
    <img src="https://r4e7m5h6.stackpathcdn.com/wp-content/uploads/2018/07/best-grocery-panniers-review.jpg"> -->

</footer>

<style>
    img {
        max-width: 100%;
    }

    footer {
        position: fixed;
    bottom: 0;
    min-height: 40%;
    left: 0;
    margin: 8px;
    }
</style>