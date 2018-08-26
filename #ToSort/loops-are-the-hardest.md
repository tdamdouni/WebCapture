# Loops Are the Hardest

_Captured: 2018-02-26 at 20:29 from [dzone.com](https://dzone.com/articles/loops-are-the-hardest?edition=364100&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=Daily%20Digest%202018-02-26)_

There is an old truism in software engineering that [199 out of 200](https://blog.codinghorror.com/why-cant-programmers-program/) job applicants can't code. Like, forget fizz buzz, can't even write a loop.

I don't know if that's true. Guess I got lucky. And I don't interview that much anyway.

But I do work with a lot of brilliant engineers in my React + D3 workshops. Go into a company, meet with a team who wants to learn some new tech, show them around for a day or two, and create a better team.

It's great.

My workshops involve a lot of coding. Practice makes perfect, and I find that a little struggle really helps the learning process.

You know, code a bit, give them a challenge, let them solve it for a few minutes, show them how it's done. It engages their brain, lets my voice rest a bit, and makes the workshop more interactive.

People love it.

Wanna know what all these brilliant, gainfully employed engineers struggle with the most?

My hardest example is a color swatch. I show them this:
    
    
    const Swatch = ({ color, width, x, y }) => (
    
    
      <rect width={width} height="20" x={x} y={y} style={{fill: color}} />
    
    
        this.width.range([0, props.width]);
    
    
              <Swatch color={this.colors[i]} width={this.width.step()} x={this.width(i)} y="0" />
    
    
    ReactDOM.render(<Colors width="300" />, document.getElementById('svg'));

See the Pen [d3 color scale](https://codepen.io/swizec/pen/oYNvpQ/) by Swizec Telleron [CodePen.i0](https://codepen.io).

It's a row of colorful rectangles that are using D3 to get colors and React to render components in a loop.

The idea is to show workshop participants how React makes code reuse simple, that D3 doesn't have to be scary, and that all the basic JavaScript and programming concepts work great. It's just code, the same kinda code you write all day.

Then I ask them to turn this row into a checkerboard.
    
    
    const Swatch = ({ color, width, x, y }) => (
    
    
      <rect width={width} height="20" x={x} y={y} style={{fill: color}} />
    
    
        this.width.range([0, props.width]);
    
    
              const color = leftToRight ? this.colors[i] : this.colors[this.colors.length-1-i];
    
    
              return <Swatch color={color} width={this.width.step()} x={this.width(i)} y={y} />
    
    
        this.yScale.range([0, props.height]);
    
    
            {d3.range(20).map(i => <ColorRow width={width} y={this.yScale(i)} leftToRight={i % 2 == 0}/>)}
    
    
    ReactDOM.render(<Checkerboard width="300" height="300" />, document.getElementById('svg'));

See the Pen [d3 color checkerboard](https://codepen.io/swizec/pen/BYdZXd/) by Swizec Teller on[ CodePen.i0.](https://codepen.io)

And I don't think anyone has ever solved it.

We're not talking beginners here. These are hard-working, smart engineers. The kind of people who grok Redux in an afternoon. Learn React in a few hours. Keep _massive_ engineering infrastructure working smoothly every day. The kind of software projects that would make me crap my pants. They do it every day. It's easy.

Systems, processes, really complex things. All easy. Many have forgotten more about software engineering than I ever knew.

Changing a loop into a nested loop? Impossible.

I mean, the simplest solution to my challenge is changing this:

To this:

Wrap the iteration in another iteration, use that to change the `y` coordinate. When you're on an even row, take colors from the left, take it from the right on odd rows.

That's all. A nested loop problem.

When we solve it together as a class, I usually create a `<Row>` component and use that in a loop. Makes nesting easier to see and makes benefits of React more apparent.

Maybe I have to change this example. Maybe loops _are_ hard and I'm just delusional.

Do people get so used to solving huge engineering problems inside massive systems that they forget how to write code?

I know designing systems is super hard and takes a special kind of brain. It's a whole different skill. How do you make this random process talk to that other mostly random process? How do you design your architecture so 50 engineers can work together? 1000 engineers? What about 10,000?

But at the cost of forgetting how loops work?

I'm both stumped and intrigued.
