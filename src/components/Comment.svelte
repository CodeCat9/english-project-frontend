<script>
  export let username;
  export let content;
  export let date;

  date = new Date(date).getTime();

  let mSecondsBetween = Date.now() - date;
  let timeBetween = toTimeFormat(mSecondsBetween);

  function toTimeFormat(mSeconds) {
    var seconds = Math.floor(mSeconds / 1000),
      minutes = Math.floor(seconds / 60),
      hours = Math.floor(minutes / 60),
      days = Math.floor(hours / 24),
      months = Math.floor(days / 30),
      years = Math.floor(days / 365);

    seconds %= 60;
    minutes %= 60;
    hours %= 24;
    days %= 30;
    months %= 12;

    if(years > 0){
        if(years == 1){
            return years + " Year";
        }
        return years + "Years";
    } else 
    if(months > 0) {
        if(months == 1){
            return months + " Month";
        }
        return months + " Months";
    } else 
    if(days > 0) {
        if(days == 1){
            return days + " Day";
        }
        return days + " Days";
    } else 
    if(hours > 0) {
        if(hours == 1){
            return hours + " Hour";
        }
        return hours + " Hours";
    } else 
    if(minutes > 0) {
        if(minutes == 1){
            return minutes + " Minute";
        }
        return minutes + " Minutes";
    }
    if(seconds > 0){
      if(seconds == 1){
            return seconds + " Second";
        }
        return seconds + " Seconds";
    }
    else{
      return "A Few Seconds"
    }
  }

</script>

<div class="comment">
  <h3 class="user">{username}</h3>
  <p class="content">{content}</p>
  <p class="date">{timeBetween} Ago</p>
</div>

<style>
  .comment {
    width: 60vw;
    min-height: 100%;
    border-radius: 3vw;
    margin-bottom: 5vh;
    padding: 3vw;
    background-color: #222d4d;
    color: #dedede;
    margin-left: 17vw;
    position: relative;
    word-wrap: break-word;
    text-align: left;
  }
  .user {
    margin-left: 3vw;
  }
  .date {
    margin-left: 50vw;
  }
  .content{
    margin-left: 5vw;
  }
</style>
